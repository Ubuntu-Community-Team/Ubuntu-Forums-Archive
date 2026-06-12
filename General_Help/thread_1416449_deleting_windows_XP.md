---
title: "deleting windows XP"
date: 2010-02-26
forum: General Help
---

### Post by bummm on 2010-02-26
Hi,
Have dual boot ubuntu 9.04/winXP (xp on its own partition, using NTFS),  havent used windows for anything for more than a year, just want to wipe that partition clean & use it for storage.
But Im not trying to get rid of the partition itself just everything on it.
would it be a problem for me to format it with gparted?  

sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3970396f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2           11907       12161     2048287+  82  Linux swap / Solaris
/dev/sda3            2551        4434    15133230   83  Linux
/dev/sda4            4435       11906    60018840   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992      499936+   6  FAT16

thank you!

---

### Post by sinurge on 2010-02-26
> **bummm said:**
> Hi,
Have dual boot ubuntu 9.04/winXP (xp on its own partition, using NTFS),  havent used windows for anything for more than a year, just want to wipe that partition clean & use it for storage.
But Im not trying to get rid of the partition itself just everything on it.
would it be a problem for me to format it with gparted?  

sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3970396f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2           11907       12161     2048287+  82  Linux swap / Solaris
/dev/sda3            2551        4434    15133230   83  Linux
/dev/sda4            4435       11906    60018840   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992      499936+   6  FAT16

thank you!
first you need to find out where your boot partition is, you would delete the partition and with it the boot as well.

go to Terminal
sudo grub
at the grub prompt > find /boot/grub/stage1

if the boot is in the partition of windows then post you delete it you will have to reinstall grub from your live cd.

to delete the partition - boot using live cd and use the partition editor, if you have gparted then use gparted and delete the partition.

---

### Post by Mark Phelps on 2010-02-26
If you're booting using GRUB, while it wrote some code to the MBR, it didn't install the bulk of its files in the NTFS partition; it installed them in a Linux-filesystem-compatible partition.

If you simply reformat the NTFS partition using GParted, you should be good to go.

---

### Post by bummm on 2010-02-28
thanks guys,
this is what i got:

grub> find /boot/grub/stage1
 (hd0,2)

when i first installed i installed XP first then Ubuntu who set up grub automatically

a few lines from my menu.lst:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

so this means I can reformat my NTFS windows partition without affecting the boot of my ubuntu?

---

