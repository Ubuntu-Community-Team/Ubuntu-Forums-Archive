---
title: "Access Partition"
date: 2010-02-13
forum: General Help
---

### Post by nonicutie on 2010-02-13
I just re-install Ubuntu because of a problem, its stuck but successfully re-install with the new one. I made two partitions, the old ones and new ones.

But how to access the old partitions?

---

### Post by Sef on 2010-02-13
Applications > Accessories > Terminal

then copy and paste this code:
```

sudo fdisk -l
```

then copy and paste your partitions here

---

### Post by nonicutie on 2010-02-13
noni@noni-laptop:~$ sudo fdisk -l
[sudo] password for noni: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb04b291

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5162    41463733+  83  Linux
/dev/sda2            5163        7296    17141355    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris
/dev/sda6            5163        6909    14032714+  83  Linux
/dev/sda7            6910        6992      666666   82  Linux swap / Solaris

Partition table entries are not in disk order

What i want to access is my file on noni@nonicutie. I re-install new ones on noni@noni~laptop. In my HD said 42GB on noni~laptop and 18GB on noni@nonicutie

---

