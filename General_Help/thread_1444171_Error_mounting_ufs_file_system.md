---
title: "Error mounting ufs file system"
date: 2010-03-31
forum: General Help
---

### Post by shiningpathb4me on 2010-03-31
This is what I'm trying to do:

[INDENT]root@bt:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d92d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          36      289138+  83  Linux
/dev/sda2              37        5142    41013945    5  Extended
/dev/sda3   *        5143        5665     4193973   a5  FreeBSD
Partition 3 does not end on cylinder boundary.
/dev/sda4   *        5665        9730    32653656   a5  FreeBSD
Partition 4 does not end on cylinder boundary.
/dev/sda5              37        1495    11719386   83  Linux
/dev/sda6            1496        2103     4883728+  82  Linux swap / Solaris
/dev/sda7            2104        5142    24410736   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006ca4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              26        3850    30720000   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdb3            3850        5763    15360000   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *        5763        5788      204632+  a5  FreeBSD
Partition 4 does not end on cylinder boundary.
root@bt:~#
root@bt:~#
root@bt:~# mount -t ufs /dev/sda4 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@bt:~#

[/INDENT]

What am I missing?

---

### Post by dess on 2010-05-20
I've used proposed "dmesg | tail", so it should be:

mount -t ufs -o ro,ufstype=ufs2 /dev/sda4 /mnt

(UFS2 by default for FreeBSD 5.3+, ufs was compiled with read-only support)

---

