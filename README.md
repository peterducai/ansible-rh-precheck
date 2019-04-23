rh-precheck
=========

A role for prechecks for following products

* RHV
* RHCF
* RHEL
  

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

```
product_yml: { rhvh43 | rhvm43 }
```

Dependencies
------------

There are no dependencies.

Example Playbook
----------------

```yaml
- name: check disk
  hosts: all
  #strategy: debug
  handlers:
    - include: handlers/handlers.yml
  tasks:
    - name: gather facts
      setup:

    - name: include tresholds
      include_vars: "{{ product_yml }}.yml"

    - name: cpu check
      include: tasks/cpu_check.yml

    - name: volume/HDD check
      include: tasks/volume_check.yml
```

and you can run it with

> ansible-playbook your_playbook.yml -u root --extra-vars="product_yml=rhvh43"


License
-------

Apache License Version 2.0

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
