---
title: "dual-boot ubuntu from LILO"
date: 2010-05-17
forum: General Help
---

### Post by nos09 on 2010-05-17
i installed Slackware ( just dont ask why - cause i dont know :P ) and then ubuntu.
now i cant boot into my ubuntu but only slackware and just wanna find a way to boot ubuntu by editing Lilo.conf file. any idea how to make it work ???
i m using 9.10 btw:popcorn:

---

### Post by nos09 on 2010-05-17
and if you need the table :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002637c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7295    58597056   83  Linux
/dev/sda2            7908       19457    92775375   83  Linux
/dev/sda3   *        7296        7907     4915890   82  Linux swap

Partition table entries are not in disk order



# the second (/dev/sda2) is ubuntu and the rest is slackware ;)

---

### Post by dandnsmith on 2010-05-17
If you edit the lilo.conf file, that isn't the end of it as, unlike GRUB, LILO needs to be re-installed to make the update effective.

---

### Post by wilee-nilee on 2010-05-17
> **nos09 said:**
> and if you need the table :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002637c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7295    58597056   83  Linux
/dev/sda2            7908       19457    92775375   83  Linux
/dev/sda3   *        7296        7907     4915890   82  Linux swap

Partition table entries are not in disk order



# the second (/dev/sda2) is ubuntu and the rest is slackware ;)

Why is your boot on swap? I haven't used slackware but that seems strange.

---

