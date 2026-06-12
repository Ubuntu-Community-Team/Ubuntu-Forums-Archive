---
title: "Remove extra HD entries In Browser Places"
date: 2010-05-09
forum: General Help
---

### Post by sandman3838 on 2010-05-09
Hello

I was checking out both NTFS Configuration Tool and Mountmanager....
I removed Mountmanager but I now have double entries for WIN_XP, WIN_7, and GAMES?  (SEE ATTACHMENT)

Ideally I would like to have it so that only the Hard Drive ARCHIVE is mounted when Ubuntu starts up and be able to Mount and Unmount the other three drives at will from File Manager (Nautilus)?

Any suggestions on how to clean this up?

Here is my HD info:

keivn@kj-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d586f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d7d0d7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15200   122093968+   7  HPFS/NTFS
/dev/sdb2           15201       30401   122102032+   f  W95 Ext'd (LBA)
/dev/sdb5           15201       30401   122102001    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66305c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08860a74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19929   160079661    7  HPFS/NTFS
keivn@kj-desktop:~$

---

