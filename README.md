setup-git-dev
=========

Role do Ansible com passos para a instalação de pacotes do Git e suas configurações em Desktop Linux.

Distribuições Suportadas pela Role
------------

- Fedora 30 ou superior
- Linux Mint LMDE 3 ou superior
- Linux Mint 19.2 ou superior
- openSUSE Leap 15.0 ou superior
- openSUSE Tumbleweed
- Ubuntu 18.04 ou superior


Tags da Role 
--------------

- main: Tag a ser utilizada em conjunto com outras tags, se alguma tag for especificada no comando.
  
- git: Executa TODAS as tasks de instalação de configuração do Git.
  
- git_install: Realiza a instalação dos pacotes do Git.
- git_config: Executa TODAS as tasks de configuração do Git.
- git_config_user: Executa as tasks de configuração de dados do usuário no Git.


Variáveis da Role 
--------------

- with_sudo: Especifica se vai ser utilizado o comando sudo na instalação (valores yes ou no). Valor padrão: yes .
- git_user_name: Representa o valor da propriedade global do Git user.name.
- git_user_email: Representa o valor da propriedade global do Git user.email.


Dependências da Role 
--------------

Linux Mint e Ubuntu:

- openssh-server. Ex.: sudo apt install openssh-server


Exemplo de Inventario
----------------

Exemplo de arquivo de hosts: pasta_invetario/hosts

    [NOME]
    IP ansible_connection=ssh ansible_ssh_user=USUARIO ansible_ssh_pass=SENHA_URUARIO ansible_become_pass=SENHA_ROOT


Especificar interpretador python 3: pasta_invetario/group_vars/all

    ansible_python_interpreter: "/usr/bin/python3"


Exemplo de Playbook
----------------

Exemplo de uso da Role com as variáveis:

    - hosts: desktop
      roles:
         - { role: setup-git-dev, git_user_name: "João",  git_user_email: "joao@gmail.com" }



Exemplo de Comandos
----------------

Comando para executar todas as tasks:

    ansible-playbook -i <caminho_inventario> <caminho_playbook>

Comando para executar a tag "git_config" (em caso de uso de tags, a tag "main" é obrigatória):

    ansible-playbook -i <caminho_inventario> <caminho_playbook> --tags "main, git_config"


License
-------

MIT