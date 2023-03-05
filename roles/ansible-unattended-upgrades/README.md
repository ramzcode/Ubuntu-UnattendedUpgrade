Role Name
=========

Ansible role to install and configure unattended-upgrades package on Ubuntu machines.

Requirements
------------

To receive e-mail notifocations a working MTA required with mailx command support, for example postfix + mailutils packages on Ubuntu machines. Corresponding Ansible role can be found [here](https://gitlab.epfl.ch/ansible-sti-roles/ansible-postfix)

Role Variables
--------------

This role contains some variables, the most cricial one is `security_updates_only`, which defaults to `true`, but when set to `false` initiates the task of templaing configuration. Variables that are used in template and their description can be found in [defaults](https://gitlab.epfl.ch/ansible-sti-roles/ansible-unattended-upgrades/-/blob/main/defaults/main.yaml).

Dependencies
------------

None

Installation
------------

In `requirements.yml`:

    - name: ansible_unattended_upgrades
      src: https://gitlab.epfl.ch/ansible-sti-roles/ansible-unattended-upgrades

In containing directory run:

    # ansible-galaxy install -r requirements.yml

Example
----------------
Including an example of how to use your role.

    - hosts: servers
      roles:
        - role: ansible_unattended_upgrades
          vars: 
            is_virtual_machine: false
            security_updates_only: false
            unattended_upgrades_email: "example@epfl.ch"

To check status use command: `systemctl list-timers apt-daily.timer`

License
-------

MIT

Author Information
------------------

Andrii Babarytskyi (https://people.epfl.ch/andrii.babarytskyi)
