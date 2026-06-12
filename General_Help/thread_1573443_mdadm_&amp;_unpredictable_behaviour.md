---
title: "mdadm &amp; unpredictable behaviour"
date: 2010-09-12
forum: General Help
---

### Post by discozohan on 2010-09-12
Hello!
  I need someone, who can explain the next:
  ( i already have /dev/md0 and /dev/md1 devices, that were created during installation for swap and root partitions )
  So:
    a) There are 2 devices, /dev/sdc and /dev/sdd
    b) On both of them i deleted old partitions and created one new partition with type "Linux raid autodetect", so /dev/sdc1 and /dev/sdd1 appeared
    c) sudo mdadm --create --verbose /dev/md2 --level=1 --raid-devices=2 /dev/sdc1 /dev/sdd1
    d) ls -la /dev/md* showed, that there is /dev/md2 device and cat /proc/mdstat showed, that md2 uses /dev/sdc1 and /dev/sdd1
    e) after reboot additional device appeared: /dev/md2p1 and cat /proc/mdstat showed, that md2 uses /dev/sdc and /dev/sdd ( whole devices, not partitions ). Sudo fdisk -l /dev/md2 showed, that there is partition table! But it doesn't exists on /dev/md0 and /dev/md1 ...

Questions:
  Why /dev/md2 has partition table, but /dev/md0 and /dev/md1 not ? Why after reboot md2 array switched from sdc1 and sdd1 to sdc and sdd ?

Thanks. Hope on some help!

---

