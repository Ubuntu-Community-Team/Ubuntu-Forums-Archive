---
title: "Recovering files after grub shat itself"
date: 2010-12-12
forum: General Help
---

### Post by franco81 on 2010-12-12
I had a laptop with Vista/Ubuntu dual boot. I took a backup of the master boot record using EasyBCD on windows. 

I had Ubuntu 10.04 installed. Grub 2 shat itself, I could no longer boot the computer, I was getting Boot Recovery> command line.

From there I could not do anything useful, I could not find the partition where grub was loaded. I could not load the live CD at all.

I now have a new hddr in the laptop with Ubuntu 10.10 installed and the old hddr connected via USB.

I can mount and view the files on the Vista partition, but cannot view any of the files on the Ubuntu partition. I just want to get the files off the Ubuntu partition at this point, not sure how to.

```

frank@rigel:~$ sudo fdisk -l
[sudo] password for frank: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ac582

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59673   479316992   83  Linux
/dev/sda2           59673       60802     9067521    5  Extended
/dev/sda5           59673       60802     9067520   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7130caf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *         192        9920    78144512    7  HPFS/NTFS
/dev/sdb3            9920       16908    56127488    7  HPFS/NTFS
/dev/sdb4           16908       19458    20478977    f  W95 Ext'd (LBA)
/dev/sdb5           16908       19425    20216832   83  Linux
/dev/sdb6           19425       19458      261120   82  Linux swap / Solaris

```

I tried using TestDisk but that did not work. Any help greatly appreciated!

---

