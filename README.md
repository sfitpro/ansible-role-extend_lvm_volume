Ansible Role: Extend LVM Volume
=========

Extend an LVM volume.

Requirements
------------

* community.general.parted module
* community.general.lvg module
* community.general.lvol module
* parted package
* gdisk package

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

```yaml
device_name: "/dev/sdb"
part_end_pct: "100%"
pv_name: "/dev/sdb1"
vg_name: "vg_app"
lv_name: "lv_app"
```

Set these variables in host_vars/hostname.yml to overwrite the default value.

The existing value can be retrieved by running `sudo lsblk`

```text
sdb                   8:16   0   30G  0 disk
└─sdb1                8:17   0   25G  0 part
  └─vg_app-lv_app   253:8    0   25G  0 lvm  /app
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers

  tasks:
  - name: extend LVM volume
    include_role:
      name: sfitpro.extend_lvm_volume
      apply:
        tags:
          - lvm
    tags:
      - never
      - lvm
```

License
-------

BSD

Author Information
------------------

This role was created by Eddie Lu.
