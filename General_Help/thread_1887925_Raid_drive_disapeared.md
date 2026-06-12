---
title: "Raid drive disapeared"
date: 2011-11-28
forum: General Help
---

### Post by Reptilian on 2011-11-28
Hey everyone

First time posting on here, could anyone try and point me in the right direction, I just installed 2x 1TB harddrives, and made a raid0, I set raid in the bios and also in disk utility, everything looked good, I copied alot of data onto the drive, then restarted now I cant seem to access the raid anymore
I can see both drive in disk utility and they say there raid there, but I cant get the raid mounted/online.
I have also tried a few suggestions on  here already regards "mdadm --assemble" 
Below is the mdadm.conf and also the results from doing a sudo fdisk -l

Im a real ubuntu nuub any help would be awesome.
ALso im using ubuntu 10.10


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

# This file was auto-generated on Sun, 27 Nov 2011 04:21:00 +1300
# by mkconf $Id$
ARRAY /dev/md/MediaCentral level=raid0 metadata=1.2 num-devices=2 UUID=aa4fdcf1:9e107439:2e690071:3ed75303 name=:MediaCentral
ARRAY /dev/md/MediaCentral level=raid0 metadata=1.2 num-devices=2 UUID=aa4fdcf1:9e107439:2e690071:3ed75303 name=:MediaCentral

``````

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bb97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b177

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30394   244139773+   7  HPFS/NTFS
/dev/sdb3           91202      121601   244188000    7  HPFS/NTFS

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d24ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4788    38453248   83  Linux
/dev/sdc2            4788        4998     1690625    5  Extended
/dev/sdc5            4788        4998     1690624   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

```

---

