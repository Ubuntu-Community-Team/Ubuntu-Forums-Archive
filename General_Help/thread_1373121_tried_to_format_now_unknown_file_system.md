---
title: "tried to format now unknown file system"
date: 2010-01-05
forum: General Help
---

### Post by ydristi on 2010-01-05
hi ,i hd just messed up with formatting a drive which was ntfs 
 now it shows that kernel can't reread the filesystem so u hve limited access

anoop@anoop-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2530252f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6081    48839665+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            6081       30400   195348318    f  W95 Ext'd (LBA)
/dev/sda5            6081       12161    48839665+  83  Linux
/dev/sda6           12162       18241    48837568+   7  HPFS/NTFS
/dev/sda7           18242       24321    48837568+   7  HPFS/NTFS
/dev/sda8           24322       30400    48829536    7  HPFS/NTFS
 
                 i tried it after unmounting all the drives but no use ..plse hlp me out

---

### Post by Leppie on 2010-01-05
have you tried formatting in windows since ntfs is not a linux native system?

---

