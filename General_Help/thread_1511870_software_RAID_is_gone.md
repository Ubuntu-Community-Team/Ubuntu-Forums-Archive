---
title: "software RAID is gone"
date: 2010-06-17
forum: General Help
---

### Post by jomex on 2010-06-17
Ubuntu hung up so I restarted my computer
now I get the error message: "out of disk" and the grub console (and I have no idea what to do there)

I'm currently working on a Live system and when I try to manually activated the software RAID I set up via Alternate installer and I get:

$ sudo dmraid -r
no raid disks

please help me before I start crying... :(

---

### Post by jomex on 2010-06-17
$ sudo fdisk -l

> 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6403    51432066    7  HPFS/NTFS
/dev/sda2            6404       19457   104856255    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ae48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5958    47850496   fd  Linux raid autodetect
/dev/sdb2            5958       30273   195312640   fd  Linux raid autodetect
/dev/sdb3           30273       30402     1034240   fd  Linux raid autodetect

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00025c92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5958    47850496   fd  Linux raid autodetect
/dev/sdc2            5958       30273   195312640   fd  Linux raid autodetect
/dev/sdc3           30273       30402     1034240   fd  Linux raid autodetect


---

### Post by jomex on 2010-06-17
when I boot up with [Shift] pressed I get into the grub menu. selecting the first entry I get:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

selecting recovery mode I get a lot of these messages:

ata4.00: status: {DRDY}
ata4.00: failed command: READ FPDMA QUEUED
ata4.00: cmd 60/01:23:45:67:89:AB:CD/00:00:00:00:00/40 tag 123 ncq 123 in res 40/01:23:45:67:89:AB:CD/00:00:00:00:00/40 Emask 0x12 (ATA bus error)


but after 3 reboots, having changed nothing, it suddenly works again...
Ubuntu is sick and cruel!

---

