pik3s
=========

Ansible role to manage Raspberry Pi K3s cluster.

Requirements
------------

None.

Role Variables
--------------

- **pik3s_vg**: Name of K3s volume group (default: `vg_k3s`)
- **pik3s_pvs**: List of comma-separated devices to use as physical volumes in the K3s volume group (default: `/dev/sda`)
- **pik3s_pvresize:** Resize physical volume to the max. available size (default: `true`)
- **pik3s_lvs**: K3s logical volumes (see default config below)
  ``` yaml
  pik3s_lvs:
    - name: lv_k3s
      size: 25%VG
      resizefs: true
      vg: "{{ pik3s_vg }}"
      mount: /var/lib/rancher/k3s
      fstype: xfs
      opts: defaults
      state: mounted
  ```

> Note: For a list of all role defaults, please see `defaults/main.yml`.

Dependencies
------------

None.

Example Playbook
----------------

``` yaml
- hosts: raspberrypi
  remote_user: pi
  become: yes
  roles:
      - tbumke.pik3s
```

License
-------

GPLv2

Author Information
------------------

Timo Bumke
