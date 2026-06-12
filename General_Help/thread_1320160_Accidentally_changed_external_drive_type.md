---
title: "Accidentally changed external drive type"
date: 2009-11-09
forum: General Help
---

### Post by atsub on 2009-11-09
Hi,

I changed it from FAT32 to Extended using the Palimpsets Disk Utility (I was trying to figure out how to change permissions). Now the drive isnt regonized by Ubuntu or XP.

sudo fdisk -l:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d1d5d1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       31575    48829567+  83  Linux
/dev/sda3           31576       38913    58942485    5  Extended
/dev/sda5           31576       38913    58942453+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf9a9a93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900649

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001    5  Extended
/dev/sdc5   ?      119512      153402   272218546+  20  Unknown

---

### Post by ezsit on 2009-11-09
> I changed it from FAT32 to Extended using the Palimpsets Disk Utility (I was trying to figure out how to change permissions). 

A word to the wise, FAT32 filesystem does not support Unix/Linux style file level permissions. You can change the permission of the mount point, but not the files residing on a FAT32 partition. You can also change the way Linux mounts a drive by default in the fstab file (lookup manual page for fstab).

As for getting the disk back to the way it was, do a search in Synaptic for a program called **testdisk**. Testdisk will recover or undue several types of partition problems. Please use google and find out how to use testdisk before proceeding. Also, backup any data you need, since filesystem work if done incorrectly, may lead to extreme data loss. :-)

---

