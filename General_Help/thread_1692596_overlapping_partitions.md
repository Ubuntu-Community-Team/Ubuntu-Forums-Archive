---
title: "overlapping partitions"
date: 2011-02-21
forum: General Help
---

### Post by ZGruk on 2011-02-21
I've been having lots of problems with my main disk, and I think their related to this.

GParted shows an error for my main filesystem "Can't have overlapping partitions" Here is the output of fdisk -lu for that disk:

```
sudo fdisk -lu /dev/sda
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003970e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    83891429    41945683+  83  Linux
/dev/sda2   *    83891430   247738364    81923467+   7  HPFS/NTFS
/dev/sda3       247738365   976768064   364514850    5  Extended
/dev/sda4       960381765   976768064     8193150   82  Linux swap / Solaris
/dev/sda5       247738491   391102424    71681967    7  HPFS/NTFS
/dev/sda6       391102488   558869219    83883366    7  HPFS/NTFS

```

---

### Post by oldfred on 2011-02-21
You somehow have swap on sda4 which is a primary partition, but it is inside the extended partition which is not allowed. 

Backup all you data just in case. And back up the partition table:
Backup partition table to text file and save elsewhere.
sudo sfdisk -d /dev/sda > PT.txt

Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

Sometimes fdisk will just reorder things without other issues, but you may have to reinstall grub or edit fstab as partitions may change.

this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

---

