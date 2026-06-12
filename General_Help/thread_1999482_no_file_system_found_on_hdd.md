---
title: "no file system found on hdd"
date: 2012-06-08
forum: General Help
---

### Post by richlyn9 on 2012-06-08
I removed my old HDD  and put it back in but now am unable to mount it.
Its shows up in Gparted  and gives an error "no file system found on hdd".

How do i fix this issue.
the Hdd in question is dev/sdd
Heres the Fdisk -l output


richlyn@richlyn-oneric:~$ sudo fdisk -l
[sudo] password for richlyn: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa64ca64c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS/exFAT
/dev/sda2        40965750    81915434    20474842+   7  HPFS/NTFS/exFAT
/dev/sda3        81915496   312576704   115330604+   f  W95 Ext'd (LBA)
/dev/sda5        81915498   143829944    30957223+   7  HPFS/NTFS/exFAT
/dev/sda6       143830008   205776584    30973288+   7  HPFS/NTFS/exFAT
/dev/sda7       205776648   267209144    30716248+   7  HPFS/NTFS/exFAT
/dev/sda8       267209208   269313659     1052226   82  Linux swap / Solaris
/dev/sda9       269313723   290937149    10811713+  83  Linux
/dev/sda10      290937213   310456124     9759456   83  Linux
/dev/sda11      310456188   312576704     1060258+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb01e6bac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            4096   976769023   488382464   83  Linux

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x667eb0aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   312580095   156290016+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xae1f8566

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   512007614   256003776   83  Linux
/dev/sdb2       512007615   976768064   232380225   83  Linux

Disk /dev/sde: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142447 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2568b5c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   625137344   312568641    7  HPFS/NTFS/exFAT
richlyn@richlyn-oneric:~$

---

### Post by richlyn9 on 2012-06-08
I tried doing Fdisk but it did not work


richlyn@richlyn-oneric:~$ sudo fdisk /dev/sdd
[sudo] password for richlyn: 

Command (m for help): p

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x667eb0aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   312580095   156290016+  83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
richlyn@richlyn-oneric:~$

Trying to mount it from Gparted give me this error.

[ATTACH]219388[/ATTACH]

viewtopic.php?f=141&t=80671

---

### Post by richlyn9 on 2012-06-08
Was googling for what best will resolve my issue.

will i be able to convert the file system not that i am unable to mount the hdd?

---

### Post by traditionalist on 2012-06-08
Do you have data on the disk you need to keep?

---

### Post by richlyn9 on 2012-06-08
> **traditionalist said:**
> Do you have data on the disk you need to keep?

yes....exactly why i don't want to format it.

---

