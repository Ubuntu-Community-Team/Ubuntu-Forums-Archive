---
title: "512B and 4KB hard drives; can I just format both starting on 64 sector?"
date: 2012-01-08
forum: General Help
---

### Post by vcrpcant on 2012-01-08
Hi,

I've experienced some problems with the new 4K hard drives.

I've read here how to deal with it:
[http://linuxconfig.org/linux-wd-ears-advanced-format](http://linuxconfig.org/linux-wd-ears-advanced-format)

What I wanted to know is if I can just format both types of hard drives just starting with sector 64 (or 2048, as I've seen somewhere adise in the web).

Like this (taken from the link above):

# fdisk -u /dev/sda

The number of cylinders for this disk is set to 121601.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10bd10bc

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (63-1953525167, default 63): _**[COLOR=Red]64[/COLOR]**_
Last sector, +sectors or +size{K,M,G} (64-1953525167, default 1953525167):
Using default value 1953525167

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.



Thanks in advance

---

### Post by vcrpcant on 2012-01-08
Just to let you know that ubuntu 10.04 seems to create partitions at block 2048 by default upon installation. 
However, and this is the point, after installation, if we want to add a new drive, fdisk creates the partition at block 63 by default.
I know that fdisk is not developed by ubuntu...
I guess I'm going to format all my drives/partitions from now on starting at block 4096.

---

