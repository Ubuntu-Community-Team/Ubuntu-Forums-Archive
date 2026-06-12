---
title: "Restoring Grub2 to boot"
date: 2010-05-28
forum: General Help
---

### Post by mawiles on 2010-05-28
I have a rather interesting situation.  I have an IDE drive with windows xp and a sata drive with ubuntu 10.04.  I have to disconnect the xp drive to get a proper boot into ubuntu (using the bios select boot drive causes the /home directory (sda5) to not mount, use to work with 9.10). How do I install grub on my xp mbr (though I hate to do that) to dual boot.  There is good documentation, but can not find documentation when more than one drive is present.  

sda = SATA Drive - ubuntu 10.04
sdb = IDE Drive - windows xp

bios is set to boot sdb first.  

If change bios to boot sda first, then ubuntu boots with error that /home is not mounted (sda5)

if use the 'on the fly' change boot order same thing as if changing boot order in bios occurs.  The solution it seems is to place grub on sdb to be able to dual boot xp and my ubuntu installation on sda.


results of fdisk -l is:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14589   117186111   83  Linux
/dev/sda2           14590       60801   371197859+   5  Extended
/dev/sda5           14590       60545   369141538+  83  Linux
/dev/sda6           60546       60801     2056288+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdc44dc4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

I would prefer to use the live CD to affect these changes.

---

