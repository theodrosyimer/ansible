## Gathering facts

for all hosts:

```sh
ansible -i inventory/file/path all -m setup
```

for a single host:

```sh
ansible 192.168.1.20 -i inventory/file/path -m setup
```

redirect the output to a file:

```sh
ansible -i inventory/file/path all -m setup > system_facts.txt
```

those facts are stored in the `ansible_facts` variable and they are used, for example, in the `when` condition:

```yaml
- name: install apache
  yum:
    name: httpd
    state: latest
  when: ansible_facts['os_family'] == 'RedHat'
```
