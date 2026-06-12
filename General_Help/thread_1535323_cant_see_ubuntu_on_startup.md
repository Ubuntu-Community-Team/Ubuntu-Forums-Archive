---
title: "cant see ubuntu on startup"
date: 2010-07-20
forum: General Help
---

### Post by Sfrekko on 2010-07-20
hi guys

i'm a newbie and after having tried ubuntu  desktop 10.4 livecd (32bit) i decided to install it but after rebooted there is no grub multiboot menu (i've also xp on this pc) so my pc starts with xp multiboot menu in which there is no ubuntu option. I didnt install ubuntu on xp partition but on another one, i format it ext3 and as mount point i set /. How can i fix it? I tried to press shift when booting but no menu appears. 
Typing fdisk -l i get some infos and the one regarding the hd where i installed ubuntu are these:

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63  sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 =  8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O  size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier:  0x8d399bc0

   Device Boot      Start         End      Blocks   Id   System
/dev/sdd1               1       60800   488375968+   7   HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255  heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 *  512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512  bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk  identifier: 0x0009859b

   Device Boot      Start         End       Blocks   Id  System
/dev/sde1   *           1       35228    282968878+   7  HPFS/NTFS
/dev/sde2           35229       60801    205415092    f  W95 Ext'd (LBA)
/dev/sde5           35229       59523    195149556    7  HPFS/NTFS
/dev/sde6           59524       60801     10265503+  83  Linux


i hope you can help me

tnk

---

### Post by Sfrekko on 2010-07-21
no one?

---

