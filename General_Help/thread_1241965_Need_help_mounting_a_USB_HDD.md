---
title: "Need help mounting a USB HDD"
date: 2009-08-16
forum: General Help
---

### Post by michael1384 on 2009-08-16
Hi there.

I have a USB hard drive. It is plugged in, it shows up in 'computer', but I cannot mount it. 

I have googl'd and seen another thread like this, tried the advice in there, but it failed. Even so, here is the output for 'sudo fdisk -l'

```
Disk /dev/sda: 1091 MB, 1091371008 bytes
64 heads, 63 sectors/track, 528 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x4aa55d6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2         528     1062432    5  Extended
/dev/sda5               2         528     1062400+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea448bcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11260    90445918+   7  HPFS/NTFS
/dev/sdb2           11261       14593    26772322+   f  W95 Ext'd (LBA)
/dev/sdb5           11261       14593    26772291   83  Linux

```

Help would be much appreciated. Thanks.

---

### Post by scouser73 on 2009-08-16
Please follow the instructions: [[COLOR="Red"]**Ubuntu: Mount External Hard Disk**[/COLOR]]("http://www.blog.highub.com/linux/ubuntu-mount-external-hard-disk/")

---

