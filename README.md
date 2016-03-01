docker-influxdb
============

[![Build Status](https://travis-ci.org/wangsha/docker-influxdb.svg?branch=master)](https://travis-ci.org/wangsha/docker-influxdb)
[![Ansible Galaxy](https://img.shields.io/badge/AnsibleGalaxy-wangsha.docker--influxdb-blue.svg)](https://galaxy.ansible.com/wangsha/docker-influxdb/)

Ansible role to manage and run the influxdb docker container.

Requirements
------------

This role has only been tested on Ubuntu 14.04. Since this uses Ansible's
docker module, you will need to ensure that a recent-ish version of `docker-py`
and `docker` are installed.

Examples
--------

Install this module from Ansible Galaxy into the './roles' directory:
```bash
ansible-galaxy install wangsha.docker-influxdb -p ./roles
```

Use it in a playbook as follows, assuming you already have docker setup:
```yaml
- hosts: 'servers'
  roles:
    - role: angstwad.docker_ubuntu
      become: true
    - role: wangsha.docker-influxdb
      become: true
```

Have a look at the [defaults/main.yml](defaults/main.yml) for role variables
that can be overridden.

If you need a playbook to set Docker itself, have a look at [angstwad.docker_ubuntu](https://github.com/angstwad/docker.ubuntu) Galaxy
role.

Known Issue:
You might encounter following errors when using this role without volume mapping.

```bash
Failed to remove container (XXX): Error response from daemon: Unable to remove filesystem for XXX: remove /var/lib/docker/containers/XXX/shm: device or resource busy
```
To work around this set `install_kernel_extras` to `true`
License
-------

[MIT](LICENSE.txt)

Author Information
------------------

- wangsha
