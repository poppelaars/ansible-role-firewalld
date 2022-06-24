# ansible-role-firewalld

[![CI](https://github.com/poppelaars/ansible-role-firewalld/workflows/CI/badge.svg?branch=main&event=push)](https://github.com/poppelaars/ansible-role-firewalld)

Setup firewalld as default firewall with custom rules.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    ssh_config:
      port: 22
      protocol: tcp
      state: enabled
      zone: public

Configures the default port for ssh usage.

    firewall_rules:
      - port: 80
        protocol: tcp
        state: enabled
        zone: public
      - port: 443
        protocol: tcp
        state: enabled
        zone: public

Setup a list to create several firewall rules.

## Dependencies

None.

## Example Playbook

    - hosts: server
      vars_files:
        - vars/main.yml
      roles:
        - { role: poppelaars.firewalld }

*Inside `vars/main.yml`*:

    firewall_rules:
      - port: 80
        protocol: tcp
        state: enabled
        zone: public
      - port: 443
        protocol: tcp
        state: enabled
        zone: public

## TODO

  - Build test inside molecule to confirm functionality of role.
  - Remove non-configured ports (diff of lists).
  - Configure firewalld.conf
