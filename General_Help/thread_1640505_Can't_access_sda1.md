---
title: "Can't access sda1"
date: 2010-12-07
forum: General Help
---

### Post by Jack LIndahl on 2010-12-07
I installed Linux on a Windows Vista system, hoping for a nice dual boot situation. That never really worked, but as long as I was able to access the Windows drive from Linux I was happy. In messing around with it some more, I even lost THAT!

Here is what fdisk tells me:


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   

Device Boot     Start     End      Blocks   Id  System


/dev/sda1   *      1    26728   214689596    7  HPFS/NTFS

/dev/sda2      26728    29138    19353600   83  Linux

/dev/sda3      29138    29271     1074177    f  W95 Ext'd (LBA)

/dev/sda4      29272    30401     9076725    c  W95 FAT32 (LBA)

/dev/sda5      29138    29271     1074176   82  Linux swap / Solaris


I really need to get into sda1. Any ideas? Thanks much!

---

