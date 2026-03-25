Role Name
=========

This Role does the following: 
- sets up a user 
- gives the user sudo priviliges 
- configures passwordless sudo for the created user
- copies the publickey of the new user, denies passsword authentication, allows pukbey authentication, denies ssh access as root
- updates the system and installs essential packages
- Tested on Debian and Rocky 
- Should work on other Debian and RedHead Distros as well

Requirements
------------

an ssh keypair for setting up pukey authentication

Role Variables
--------------

main.yaml: 

- server_setup_new_user --> enter your desired username
- server_setup_pub_key --> enter your publickey
- server_setup_packages --> enter a list of apt packages 
**do not remove sudo. if you do passwordless sudo will not work**
- server_setup_dnf_packages --> enter a list of dnf packages
**do not remove sudo. if you do passwordless sudo will not work**
- server_setup_password --> password for your new user 
**Encrypt your variable with the following command, where password stands for your password**
`ansible-vault encrypt_string 'server_setup_password' --name 'password'`
or if your are using a password file
`ansible-vault encrypt_string --vault-password-file a_password_file 'server_setup_password' --name 'password'`


Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

- name: Setup a Server.
  hosts: all
  gather_facts: true
  become: true
    
  roles:
   - server_setup

License
-------

GNU_GPL_V2

