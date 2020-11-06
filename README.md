# Ansible Role : load_balancer

Ansible Role for Jakarta Project's moodle load balancing through HAProxy.

This role configures two Debian 9 machine through different steps :
- Creates a user 'sysadmin' for non-root logins
- Installs the correct network configuration according to Jakarta's IP adressing plan
- Installs HAProxy and configures it
- Installs HeartBeat and sets up the cluster
- Restarts both HAProxy, HeartBeat and networking services

Requirements
------------

- Debian 9 with minimal install
- Two network adapters
- SSH installed and sshd.service enabled
- **sudo** package installed
- Two bridged interfaces using the **.20.26 and .20.27/26 IPs** on the main node
- Two bridged interfaces using the **.20.24 and .20.25/26 IPs** on the passive node
- DNS set to 192.168.4.2 in */etc/resolv.conf*
- [User 'Ansible' already configured](https://github.com/nickjj/ansible-user)

**Note** : A template Debian 9 VM **with all requirements satisfied** is available [here](https://192.168.4.16/Equipe_1_Jakarta/debian9-template).

Example Playbook
----------------

```
- name: Deploy load balancing for Jakarta
  hosts: "{{hosts}}"
  remote_user: ansible
  tasks:
  - import_role:
      name: load_balancer
      tasks_from: install
```

Author Information
------------------

* **Toréa TESSIER** - <torea.tessier@reseau.eseo.fr> - [Jakarta Project](https://192.168.4.16/Equipe_1_Jakarta/)



