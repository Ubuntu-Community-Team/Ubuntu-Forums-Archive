---
title: "Mounting problems after the upgrade to 9.10"
date: 2010-04-11
forum: General Help
---

### Post by Groll on 2010-04-11
Hello,

After the upgrade to ubuntu 9.10 I noticed that Ubuntu didn't mount all of my partitions. I checked fstab and the ones that were not mounted were missing so I decided to add the manually.

They are the last three entries (I coudn't get their UUIDs with the blkid command)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=00da4c03-59ca-4a71-9681-dd82ccec42ab /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=9d7f6418-58e1-4e54-a7f6-f88bc0cc3f13 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sda1
/dev/sda1    /media/WinXP      ntfs-3g      quiet,defaults,locale=en_US.utf8,umask=0    0 0
# /dev/sda2
/dev/sda2    /media/Exp3win    ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
/dev/sdb1    /media/Data      ntfs-3g      quiet,defaults,locale=en_US.utf8,umask=0    0 0
```However when I typed &quot;mount -a&quot; I got the following error:
```
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org
mount: special device /dev/sda2 does not exist
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org
```The output of &quot;fdisk -l&quot;
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc20aa290

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       19457    94847760   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa556ad93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a2d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281   83  Linux

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd628d628

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        4660    37431418+  83  Linux
/dev/sdd2            4661        4865     1646662+   5  Extended
/dev/sdd5            4661        4865     1646631   82  Linux swap / Solaris
```cat /proc/partitions
```
major minor  #blocks  name

   8        0  156290904 sda
   8       16  156290904 sdb
   8       32  625131864 sdc
   8       33  625129281 sdc1
   8       48   39082680 sdd
   8       49   37431418 sdd1
   8       50          1 sdd2
   8       53    1646631 sdd5
 252        0  312581760 dm-0
 252        1  156280288 dm-1
```When I looked at Gparted I saw that Ubuntu has detected two of my disks as raid (that wasn't the case in 9.04). They were once raid 0 but not anymore. That is probably what causes the problem since the partitions that don't open are on these disks. 

RAID is at /dev/mapper/nvidia_dbehidfe and this is the output of "sudo fdisk /dev/mapper/nvidia_dbehidfe"
```

The number of cylinders for this disk is set to 38914.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):
```Any ideas? :confused:

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
Did you try ```
sudo blkid
``` to get UUID? What was the output?

---

### Post by Groll on 2010-04-11
> **Sin@Sin-Sacrifice said:**
> Did you try ```
sudo blkid
``` to get UUID? What was the output?

No output for the partitions that are missing. That's not the problem though...  I searched and saw the there is some bug going on with dmraid. Here's a similar thread: [http://ubuntuforums.org/showthread.php?t=1310344](http://ubuntuforums.org/showthread.php?t=1310344)
I solved my problem with "sudo apt-get remove dmraid".

---

