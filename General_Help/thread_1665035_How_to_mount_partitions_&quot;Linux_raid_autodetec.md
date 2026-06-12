---
title: "How to mount partitions &quot;Linux raid autodetect&quot;?"
date: 2011-01-11
forum: General Help
---

### Post by davidhoenig on 2011-01-11
I have an Iomega Home Media Network Drive (small, cheap, NAS)

[http://go.iomega.com/en-us/products/network-storage-desktop/home-network-hard-drives/home-media/](http://go.iomega.com/en-us/products/network-storage-desktop/home-network-hard-drives/home-media/)

Recently the controller died and it will no longer connect to my network. Before I take it to our local electronics recycler, I'd like to recover the data from the drive.

I removed the bare drive from the NAS and plugged it into my Ubuntu 10.10 PC. I see the following:

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001cf00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4         515     4112640   fd  Linux raid autodetect
/dev/sdb2             516      121601   972623295   fd  Linux raid autodetect
/dev/sdb3               1           3       24097   da  Non-FS data

I believe the sdb2 is the data partition I want to mount, but it appears to be part of a RAID array. The NAS only contains one drive, so is sdb1 the other part of the RAID array?

If I look in the system partition of the drive I see in /etc/fstab:

# line needed for quotas, noauto makes mount -a skip it so nasmon can mount it correctly
/dev/sda2		/nethdd/	mkswxfs				defaults,noauto		0 0

But I have never heard of type "mkswxfs", nor has googling returned any information.

I assume I need to create a RAID array out of sdb1 and sdb2 but I am new to this. Can anyone recommend a suggestion?

Also, on the system partition:

$ cat etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Wed, 30 Sep 2009 13:24:23 +0000
# by mkconf $Id$

---

### Post by davidhoenig on 2011-01-17
I solved my own problem: it turns out RAID was just a red herring. The real problem was a corrupted XFS journal. After running xfs_repair and zero-ing out bad entries in the log, I was able to mount the partition. I still got some I/O errors when trying to copy the data off, so there was a hardware failure on the disk, but I was able to get most of my files.

Hopefully this helps someone else with a corrupted XFS filesystem.

---

