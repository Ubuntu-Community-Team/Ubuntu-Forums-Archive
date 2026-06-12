---
title: "At boot linux complains mount point (/tmp) is not ready"
date: 2011-05-28
forum: General Help
---

### Post by Capone on 2011-05-28
Sometimes when i boot, the kernel complains /tmp is not ready and asks for manual mount or skip mounting.

Does anyone else also experience this?

---

### Post by LowSky on 2011-05-28
on a normal install /tmp is usually a folder in the / partition. if its failing to mount it could mean something is failing. probably the hard drive olr mayby the motherboard. check first for loose wires to make sure it isnt something that simple

---

### Post by Capone on 2011-05-28
ok, this is a laptop.
and this is solved by manually mounting the partition from the recovery shell and the boot continues.

Sounds like a problem with udev...

---

### Post by Capone on 2011-05-28
i wonder if it's related with this bug:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/753853](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/753853)

i'm using LVM

lisrferre@porf0003n:~$ sudo lvdisplay  | grep "LV Name"
  LV Name                /dev/vg0/lv_root
  LV Name                /dev/vg0/lv_var
  LV Name                /dev/vg0/lv_swap
  LV Name                /dev/vg0/lv_tmp
  LV Name                /dev/vg0/lv_home

---

