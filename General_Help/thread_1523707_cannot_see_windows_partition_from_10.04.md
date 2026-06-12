---
title: "cannot see windows partition from 10.04"
date: 2010-07-04
forum: General Help
---

### Post by smtouhid on 2010-07-04
Dear,
I cannot see my windows partition from ubuntu 1.04. Also cannot mount pen drive.

---

### Post by khuttger on 2010-07-04
have you installed NTFS support?

```
sudo aptitude install ntfs-3g -y
```

---

### Post by Rubi1200 on 2010-07-04
Can you post the results of 

```
sudo fdisk -l
```

Lowercase L not a 1.

Thanks.

---

### Post by smtouhid on 2010-07-04
See the result
# fdisk -l

[QUOTE=
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb1dfb1df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3060    24579418+   7  HPFS/NTFS
/dev/sda2            3061        8801    46114552    f  W95 Ext'd (LBA)
/dev/sda3            8802        8832      249007+  83  Linux
/dev/sda4            8833       10011     9470317+  83  Linux
/dev/sda5            3061        5227    17406396    b  W95 FAT32
/dev/sda6            5228        7267    16386268+   b  W95 FAT32
/dev/sda7            7268        8552    10321731   83  Linux
/dev/sda8            8553        8801     2000061   82  Linux swap / Solaris

[/QUOTE]

---

### Post by dino99 on 2010-07-04
is ntfsprogs installed ?

mountmanager is an easy tool to manage partitions & devices

---

### Post by smtouhid on 2010-07-04
After updating all packages from update manager problem solved!

Thank to you all

---

