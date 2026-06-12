---
title: "Error mounting: mount exited with exit code 2"
date: 2011-09-29
forum: General Help
---

### Post by Kiran Sagar on 2011-09-29
I have been using Ubuntu for a few months and all was going fine, but now I am not able to mount any of the drives (sda 2 & sda 3). 
i used "sudo fdisk -lu" on the terminal 

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      144584       72261   de  Dell Utility
/dev/sda2   *      145408   356159487   178007040    7  HPFS/NTFS
/dev/sda3       356161536   563654655   103746560    7  HPFS/NTFS
/dev/sda4       563656714   625141759    30742523    5  Extended
/dev/sda5       563656716   625141759    30742522   83  Linux

```

Please help me with this.
Thanks in advance

---

### Post by dino99 on 2011-09-29
post here your /etc/fstab please
and: sudo blkid

---

