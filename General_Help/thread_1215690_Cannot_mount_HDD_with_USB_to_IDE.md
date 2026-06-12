---
title: "Cannot mount HDD with USB to IDE"
date: 2009-07-17
forum: General Help
---

### Post by k50aker on 2009-07-17
I've posted this in another category  on this forum but i got no  reply,  so here  i go  again.

i'm booting from a live cd and trying to connect a laptop hdd with a USB to IDE cable to my desktop, and i get an error when i mount it.

Here's the error:
$MFTMirr does not match $MFT (record 3). Failed To mount '/dev/sdi2': Input/output error NTFS is either inconsistent, or you have hardware faults.

fdisk -l came up with this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x578b578b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sdb2           10200       19452    74324722+   5  Extended
/dev/sdb5           10200       10691     3951958+  82  Linux swap / Solaris
/dev/sdb6           10692       19452    70372701   83  Linux

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x551b0dcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b5188c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdi: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1           7       56196   de  Dell Utility
/dev/sdi2   *           8        4373    35069895    7  HPFS/NTFS
/dev/sdi3            4374        4863     3935925   db  CP/M / CTOS / ...
ubuntu@ubuntu:~$ 
-------------------------

the disk with the problem is the 40Gb.

i tried to look for a solution and i couldnt find one, and i would really appreciate if some1 can guide me through this.

Thanks,
k50aker

---

