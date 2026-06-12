---
title: "RAID array not starting up after upgrade"
date: 2011-05-25
forum: General Help
---

### Post by BaldNomad on 2011-05-25
I have a RAID 5 array that will no longer start up properly.

I think this started happening several months ago (just now getting to fixing it) after an Ubuntu upgrade, not sure which version it was.

I set this up a couple of years ago and have had no trouble with it until this.  I'm sure I set it up using some guide I found online somewhere and managed to get it working, but now I'm not sure where to start with the troubleshooting.

I tried to fix this problem once before, and I suspect it has something to do with my 3 drives getting assigned the wrong identifiers, possibly caused by a switch to the UUID drive ID method?  I'm sure I did not set these disks up using their UUID when I did the setup, unless this is done automatically somehow.

My boot disk is not supposed to be part of the RAID, and I am able to boot the machine so that is working.  In addition to the boot drive, I have 3 drives in the RAID setup.

There is data on the array that I don't wish to lose.  I need to correct whatever is wrong with the configuration so that the array will mount in the way it should...

I'm a bit of a noob at this, but after some searching I have collected the output of the following commands, I don't know exactly what all of this means but I'm hoping there are some useful nuggets in there someone can help me identify!

fdisk -l:

```
Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7be1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35836   287852638+  83  Linux
/dev/sda2           35837       36483     5197027+   5  Extended
/dev/sda5           35837       36483     5196996   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c005e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059d0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   83  Linux

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a33b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001   83  Linux

```

so, this means that the RAID should be defined using the three 1.5GB drives, sdb, sdc, and sdd.  sda is my primary boot drive.

mdadm --detail /dev/md0:

```
mdadm: metadata format 00.90 unknown, ignored.
mdadm: md device /dev/md0 does not appear to be active.
```

cat /etc/mdadm/mdadm.conf:

```
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

# This file was auto-generated on Mon, 06 Jul 2009 12:46:31 -0500
# by mkconf $Id$
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=9e6c6d69:0c0a09df:2317d6f0:1330f7fd
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1
```

that last line looks like it is trying to define the array using disks a,b,c instead of b,c,d?

cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=5b4d7846-6a6a-4f02-bf94-0291087ed911 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=c102e5e7-a03f-429e-8e37-e8796c2fae12 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/md0 /var/share auto defaults 0 3
```

blkid:
```
/dev/sda1: UUID="5b4d7846-6a6a-4f02-bf94-0291087ed911" TYPE="ext3" 
/dev/sda5: UUID="c102e5e7-a03f-429e-8e37-e8796c2fae12" TYPE="swap" 
/dev/sdb1: UUID="9e6c6d69-0c0a-09df-2317-d6f01330f7fd" TYPE="linux_raid_member" 
/dev/sdc1: UUID="9e6c6d69-0c0a-09df-2317-d6f01330f7fd" TYPE="linux_raid_member" 
/dev/sdd1: UUID="9e6c6d69-0c0a-09df-2317-d6f01330f7fd" TYPE="linux_raid_member" 
```

---

### Post by BaldNomad on 2011-05-25
one more:


cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdd1[2](S)
      1465135936 blocks
       
md0 : inactive sdc1[1](S) sdb1[0](S)
      2930271872 blocks
       
unused devices: <none>

```

---

