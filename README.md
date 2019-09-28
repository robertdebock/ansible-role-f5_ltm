f5_ltm
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-f5_ltm"><img src="https://travis-ci.org/robertdebock/ansible-role-f5_ltm.svg?branch=master" alt="Build status" align="left"/></a>

Configure an F5 LTMs nodes, pool, pool members and virtual servers.

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - robertdebock.f5_ltm
```

The machine you are running this on, may need to be prepared.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - robertdebock.bootstrap
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for f5_ltm

# Connection details for the F5 LTM.
# f5_ltm_provider:
#   server: 192.168.1.254
#   user: root
#   password: password
#   server_port: 8443
#   validate_certs: no

# General settings for the F5 LTM.
f5_ltm_partition: Common
f5_ltm_hostname: f5.example.com
f5_ltm_timezone: "Europe/Amsterdam"
f5_ltm_ntp_servers:
  - 1.1.1.1
  - 8.8.8.8

# The list of nodes.
# f5_ltm_nodes:
#   - name: node1.example.com
#     host: 192.168.1.1
#   - name: node2.example.com
#     host: 192.168.1.2

# The list of pools.
# f5_ltm_pools:
#   - name: pool1.example.com
#     lb_method: http_pool
#     monitors: /Common/http
#     monitor_type: and_list

# The list of pools and their members.
# f5_ltm_pool_members:
#   - name: pool1.example.com
#     members:
#       - name: node1.example.com
#         port: 80
#       - name: node2.example.com
#         port: 80

# The list of virtual_servers.
# f5_ltm_virtual_servers:
#   - name: virtual_server1.example.com
#     pool: pool1.example.com
#     destination: 192.168.1.254
#     port: 443
#     enable_vlans: all
#     all_profiles:
#       - http
#       - clientssl
#       - oneconnect
#     snat: Automap
```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap

```

This role uses the following modules:
```yaml
---
- bigip_device_ntp
- bigip_hostname
- bigip_node
- bigip_pool
- bigip_pool_member
- bigip_virtual_server
- include
- service
```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/f5_ltm.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.7|ansible 2.8|ansible devel|
|------------|-----------|-----------|-------------|
|alpine-edge*|yes|yes|yes*|
|alpine-latest|yes|yes|yes*|
|archlinux|yes|yes|yes*|
|centos-6|yes|yes|yes*|
|centos-latest|yes|yes|yes*|
|debian-stable|yes|yes|yes*|
|debian-unstable*|yes|yes|yes*|
|fedora-latest|yes|yes|yes*|
|fedora-rawhide*|yes|yes|yes*|
|opensuse-leap|yes|yes|yes*|
|ubuntu-devel*|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes*|
|ubuntu-rolling|yes|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.




Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-f5_ltm) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-f5_ltm/issues)

To test this role locally please use [Molecule](https://github.com/ansible/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and set a region using `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
