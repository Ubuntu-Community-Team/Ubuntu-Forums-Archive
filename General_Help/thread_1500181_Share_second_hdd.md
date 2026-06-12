---
title: "Share second hdd"
date: 2010-06-02
forum: General Help
---

### Post by Papa Oso on 2010-06-02
Hi I installed a second hdd with the intention of share it over my home network. After formated on fat32 (I own one windows machine) What I did was logged as root create the files I want to share and right click on it sharing option and check mark on sharing this folder and allow to create and delete files. When I try to access from my other computer ask me for a password and domain. I use the same password in all the computer on my net but dont let me access. Any Idea?
Thanks in advance

marcos@desktop-1:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000822e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6994    56174592   83  Linux
/dev/sda2            6994        7298     2438145    5  Extended
/dev/sda5            6994        7298     2438144   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc5256cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312571192+  83  Linux

---

