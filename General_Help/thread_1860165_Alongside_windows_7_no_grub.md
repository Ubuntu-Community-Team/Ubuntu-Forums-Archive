---
title: "Alongside windows 7 no grub?"
date: 2011-10-14
forum: General Help
---

### Post by Unngenant on 2011-10-14
I installed Ubuntu on the hard disk where Windows already installed 7. After installation, however, I was not able to see grub and to boot to Ubuntu 11.10, boot directly goes to Windows ... I got this when I type in terminal:

[PHP]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b8f4d12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2668795903  1334396928    7  HPFS/NTFS/exFAT
/dev/sda2      2668795904  3907024895   619114496    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40eaab13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848  2910953831  1455373492    7  HPFS/NTFS/exFAT
/dev/sdb3      2910955518  3907028991   498036737    5  Extended
/dev/sdb5      2910955520  3890298879   489671680   83  Linux
/dev/sdb6      3890300928  3907028991     8364032   82  Linux swap / Solaris

sudo parted -l
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1366GB  1366GB  primary  ntfs         boot
 2      1366GB  2000GB  634GB   primary  ntfs


Model: ATA WDC WD2002FAEX-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   1490GB  1490GB  primary   ntfs
 3      1490GB  2000GB  510GB   extended
 5      1490GB  1992GB  501GB   logical   ext4
 6      1992GB  2000GB  8565MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Cant have a partition outside the disk! [/PHP]

Yes I have 2 hard drives but in the same where is windows 7 is installed Ubuntu.


[[img]http://s2.postimage.org/3tsqrsv8/parti.png[/img]](http://postimage.org/image/3tsqrsv8/)

[[img]http://s2.postimage.org/3tueb5d0/parti2.png[/img]](http://postimage.org/image/3tueb5d0/)

What can I do to get boot options right?

---

### Post by Mark Phelps on 2011-10-14
You may need to reinstall GRUB -- but BEFORE you do that, since that brings a risk of corrupting Win7 and rendering it unbootable, do yourself a favor.  Boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  This will come in handy later if your Win7 boot loader gets damaged when attempting to reinstall GRUB.

---

