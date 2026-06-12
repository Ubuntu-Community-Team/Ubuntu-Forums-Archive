---
title: "Unable to Mount/Format USB"
date: 2011-03-06
forum: General Help
---

### Post by Rushyang on 2011-03-06
Hiya fellas...

I have USB which is already not recognised windows and when I insert while ubuntu is on.. It does recognise it.. But does not allow me to mount, no matter through command line, or won't let me format it through disk utility. 

~ When I do `sudo fdisk -l` .. there is no entry of my USB..

~ BUT, when I do `sudo lsusb`.. I have results as follow..
> 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0736 Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:1234 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The entry with Microsoft Corp. name is my Microsoft SideWinder mouse. 
and second last I assume is my USB, as I have no other active USB connections.

Any solution?

---

### Post by muemarco on 2011-04-29
I have exactly the same problem!

with sudo fstab -l I get the following output:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ec76a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29637   238053376   83  Linux
/dev/sda2           29637       30402     6142977    5  Extended
/dev/sda5           29637       30402     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x61379ba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953513440+   7  HPFS/NTFS

when  I run lsusb, I get:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0d46:4081 Kobil Systems GmbH mIDentity Basic/Classic (installationless)
Bus 003 Device 003: ID 03f0:5511 Hewlett-Packard DeskJet F300 series
Bus 003 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-Port Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

amazingly the DeskJet printer works but I have no chance to access my usb-memory stik. (Bus 003 Device 004: ID 0d46:4081 ...)

Any help?

---

### Post by kstella on 2011-05-01
I think I have a similar problem; I'm trying to format my USB using Disk Utility. When I first click format, it tells me that the disk is still mounted. So I go and eject the disk, but when I click format again, it tells me "Error creating partition table: helper exited with exit code 1: cannot open /dev/sdc: no medium found." :confused:

---

