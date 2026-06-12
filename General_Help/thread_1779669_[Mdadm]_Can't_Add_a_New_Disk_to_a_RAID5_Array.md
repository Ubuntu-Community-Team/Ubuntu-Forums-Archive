---
title: "[Mdadm] Can't Add a New Disk to a RAID5 Array"
date: 2011-06-10
forum: General Help
---

### Post by terrigat on 2011-06-10
I am trying to build a new array after adjusting TLER on my disks, which permanently changed some of the drives sizes. I am not sure if the following inconsistencies are related to the newly mismatched drive sizes.

Using:
```
mdadm --create --auto=md --verbose --chunk=64 --level=5 --raid-devices=4 /dev/md1 /dev/sdd /dev/sde /dev/sdf /dev/sdg
```Nets me (build-time was two full days):
```
md1 : inactive sdd[0](S) sdg[4](S) sde[1](S) sdf[2](S)
      7814052127 blocks super 1.2
```Thats a lot of spares

This:
```
# mdadm --assemble --force /dev/md1 /dev/sdd /dev/sde /dev/sdf /dev/sdg
mdadm: /dev/md1 assembled from 2 drives and 2 spares - not enough to start the array.
```Doesn't seem to help

fdisk of the identical drives:
```

Disk /dev/sdd: 2000.4 GB, 2000397852160 bytes
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
Disk /dev/sdf: 2000.4 GB, 2000397852160 bytes
Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes

```On a side note, since I'm recreating my array from scratch, I was wondering if anyone here knows of any optimized settings I could use.   I've got 3Tb of data to transfer, so lots of test material.

These are Western Digital First Generation 2TB Green Drives (WD20EADS-00R6B0) with WDidle3 fix applied & TLER=ON.  These are pre Advanced Format (aka not 4K).


```
mkfs.ext4 -E stripe-width=48,stride=16 /dev/md1
```

---

### Post by terrigat on 2011-06-11
**Background Information**

It's an old array using 4 x WD20EADS-00R6B0 drives (2TB each). Commands:

```
mdadm --create --auto=md --verbose --chunk=64 --level=5 --raid-devices=4 /dev/md1 /dev/sda /dev/sdb /dev/sdc /dev/sdd

mkfs.ext4 -E stripe-width=48,stride=16 /dev/md1
```Since restarting  my  server with a fresh Natty install, I found the old performance  issues  had gotten out of hand*. Diagnostic time!!

```
smartctl -t short /dev/sd[efgh]
smartctl --all /dev/sd[efgh]

```*no errors*

```
 mdadm -E /dev/sd[efgh]
```*clean*

```
 cat /proc/mdstat
```*active*

```
top
```*CPU & RAM not overloaded*

The old Realtek 8111C driver issue
[I]happens even from an internal hard drive and plenty fast over the network from the other drives
[/I]
AMD SB710 southbridge
*no known issues*

WD20EADS-00R6B0
*raid performance issues*

Being EADS, which are specifically non-raid compatible but with the TLER  still adjustable because these were first generation, I thought that  WDidle3 repairing them & then WDTLERing each disk separately while  rebuilding the array between was fairly straightforward (noob!!!)



*
Copying 300GB's of data from an internal SATA hard drive to the array took 34 hours.
Copying under half GB averaged 120mb/s for samba.
Copying half GB to 2GB averaged 7-11mb/s for samba.
Copying over 2GB results in errors / corrupted files.

---

### Post by terrigat on 2011-06-12
```

Disk /dev/sdg: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa6775b46

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdh doesn't contain a valid partition table

```
How can I get /dev/sdg the same as /dev/sd[efh]?

181,856 bytes smaller. How?

---

### Post by ian dobson on 2011-06-12
Hi,

Create a partition on the drive, then add the partition to the array (/dev/sdg1)

Regards
Ian Dobson

---

### Post by terrigat on 2011-06-12
Will that work?

These drives technically don't have partitions, so I would need to add as a full drive (/dev/sdg).

Does this suggest that attaching a partition to the drive will correct the smaller reported size in fdisk?

---

### Post by ian dobson on 2011-06-12
Hi,

mdadm can use any block device (A harddisk, a partition or a file). So just create a partition on your empty harddisk that's the same size as the other devices, the add that partition to mdadm.

This is the mdadm.conf I use on my video server:-
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR i.dobson@planet-ian.com

# definitions of existing MD arrays

# This file was auto-generated on Sat, 19 May 2007 17:11:35 +0200
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

DEVICE  partitions

ARRAY /dev/md0 level=raid1 num-devices=4 metadata=0.90 UUID=4c164070:fb03e2c5:f1249533:23a13f7b
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
ARRAY /dev/md1 level=raid5 num-devices=4 metadata=0.90 UUID=bae99b90:153e32ae:f1249533:23a13f7b
   devices=/dev/sda2,/dev/sdb2,/dev/sdc2,/dev/sdd2
ARRAY /dev/md2 level=raid0   num-devices=3 UUID=73a20df2:2fd838f5:f1249533:23a13f7b
   devices=/dev/sde1,/dev/sdf1,/dev/sdg1
```

Using partitions that are abit smaller that the actual drive size makes life easier in the future. A 1Tb harddisk isn't necessarly the same size as a 1Tb drive from a different manufacturer/or a different series from the same manufacturer.

Regards
Ian Dobson

---

### Post by YesWeCan on 2011-06-12
It occurs to me that sdg is physically smaller than sdh by 1081856 bytes.
When you add a new device it must have at least the same size as the existing ones, or the smallest existing partition included in the array.
So it seems to me that you may have to shrink the array size to something smaller than sdg before you can add sdg.

---

### Post by terrigat on 2011-06-12
> **YesWeCan said:**
> It occurs to me that sdg is physically smaller than sdh by 1081856 bytes.
When you add a new device it must have at least the same size as the existing ones, or the smallest existing partition included in the array.
So it seems to me that you may have to shrink the array size to something smaller than sdg before you can add sdg.

This is what I fear having to do. I may have trouble digging up enough separate space to hold all the current data as I rebuild it.  The trouble is, these hard drives are / were identical before turning on TLER for /dev/sdg.

---

### Post by YesWeCan on 2011-06-13
This may be helpful: [http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)

In summary, you need to shrink your data partition, then shrink the array, then expand the data partition. Finally add the new disk and resync.

---

### Post by psusi on 2011-06-13
> **terrigat said:**
> This is what I fear having to do. I may have trouble digging up enough separate space to hold all the current data as I rebuild it.  The trouble is, these hard drives are / were identical before turning on TLER for /dev/sdg.

Weird, so turning on TLER caused the drive to shrink by just over a MB?

---

### Post by YesWeCan on 2011-06-13
This is a tricky problem. Is it the case that there are other ways in which the number of addressable sectors can reduce from "new"?

Should there be/is there a guideline for setting up mdadm arrays that prescribes a precautionary unused gap on each disk? To make the array tolerate small variations in disk sectors among disks with the same nominal capacities?

---

### Post by psusi on 2011-06-13
Drives certainly aren't supposed to change size on you.

---

### Post by terrigat on 2011-06-14
I really can't say I expected turning TLER on would use up drive space. It just seems odd.

I am currenty rsync'ing the data before trying anything else. Slow as hell transferring off of it before; doubly so with a missing member. And still no promises of fixed* performance.

If I can get my bytes back, I'd love to try that first before messing with the partition size. Heck, if I was going to attempt a resize, I'd prefer to reformat and start again.

*
Not improved performance; fixed. No drive should error out like this is currently doing & it didn't do so before when using jaunty.

---

### Post by terrigat on 2011-06-14
> **YesWeCan said:**
> This is a tricky problem. Is it the case that there are other ways in which the number of addressable sectors can reduce from "new"?


The drive still has the same amount of sectors / cylinders as the other drives according to fdisk

Disk /dev/sdg: 2000.4 GB, 2000397852160 bytes 255 heads, 63 sectors/track, 243201 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical)

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes 255 heads, 63 sectors/track, 243201 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical)

---

### Post by psusi on 2011-06-14
What if you turn TLER back off?

---

### Post by terrigat on 2011-06-15
Don't wish to muck with settings until the data is safe again. Was hoping to test for space loss being consistent across multiple wd20eads.

---

### Post by psusi on 2011-06-15
Then turn TLER back off on that drive, see if the space comes back, then put it back in the raid and let it resync.  Then try another drive if you want.

---

### Post by YesWeCan on 2011-06-15
> **terrigat said:**
> The drive still has the same amount of sectors / cylinders as the other drives according to fdisk

Disk /dev/sdg: 2000.4 GB, 2000397852160 bytes 255 heads, 63 sectors/track, 243201 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical)

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes 255 heads, 63 sectors/track, 243201 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical)
I don't understand the numbers fdisk gives.

According to fdisk, there are 243201 cylinders of 16065 sectors = 3,907,024,065 sectors. There are 512 bytes per sector so the total bytes = 2,000,396,321,280. But this total bytes is less than is reported for either sdg or sdh!

:-k

Things do not add up. Of course, the reported number of heads and cylinders is a lie. In reality, there aren't 255 heads. It just reports it like this to comply with conventions. Perhaps the reported byte count is accurate (?) and this is what mdadm uses to compute array component size.

---

### Post by psusi on 2011-06-15
That is because the number of sectors is not an even multiple of the computed cylinder size.  Basically you should just ignore CHS since they are a meaningless vestige of days gone by.

---

### Post by YesWeCan on 2011-06-16
> **psusi said:**
> That is because the number of sectors is not an even multiple of the computed cylinder size.  Basically you should just ignore CHS since they are a meaningless vestige of days gone by.
Is this a "feature" of fdisk or something the disk reports? It is a tell that 255 heads are reported (1 byte's worth) as if it saturates the head count before expanding the cyclinder count. I wonder why it concocts a fictitious  geometry instead of simply reporting the sector size and sector count? Better still, report the actual number of heads and cylinders.

---

### Post by psusi on 2011-06-16
The numbers are synthesized by fdisk.  There is no such thing as an "actual" number of heads and cylinders anymore.  Use the u command or switch to put fdisk into sector mode instead of cylinder mode.

---

### Post by terrigat on 2011-06-18
Now that the data has been removed I tested TLER switching.
WARNING: /dev/sd# keeps changing so this post will be difficult to compare to the previous posted info
The space does not come back on /dev/sdc. As a matter of fact, /dev/sde becomes the same size as /dev/sdc but d/f stay the original size even with TLER turned on.

fdisk -l
```

...
Disk /dev/sdc: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa6775b46

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table
...

```The method of switching involves changing the BIOS setting AHCI to Native IDE.
Booting into a DOS ( WIN98 ) environment.
Running TLER-ON.BAT (v1.03) then check using TLERSCAN.BAT.
Changing the BIOS back and reboot.

Serial Number differences:
/dev/sdc
WD-WCAVY1321**782**
/dev/sdd
WD-WCAVY1321**913**
/dev/sde
 WD-WCAVY1321**799**
/dev/sdf
WD-WCAVY1321**943**

---

### Post by terrigat on 2011-06-18
Well, I'm recreating that array and am hoping that the newly mismatched drives don't impact performance too much.

Advice welcome.

Updated title and first post to match.

---

### Post by terrigat on 2011-06-21
Yay!!
New error that I can't find a reference to online.

Outside of trying to create the array again (with the possibility of another 48hr resync that fails the same way), any clues as to why the array assembles with all drives as spares?

---

