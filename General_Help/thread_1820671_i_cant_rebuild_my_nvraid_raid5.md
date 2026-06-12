---
title: "i cant rebuild my nvraid raid5"
date: 2011-08-07
forum: General Help
---

### Post by xtianF on 2011-08-07
i cant rebuild my nvraid raid5 after a motherboard failure and replacement.
The thing that lead up to what i believe was a motherboard failure was installing a 3ware driver for a 9650 se card, i cant find any info on whether you can  have a nvraid and a 3ware running simultaneously.
anywho i tryed the stuff listed here.
[http://ubuntuforums.org/showthread.php?t=707322](http://ubuntuforums.org/showthread.php?t=707322)
but no go!

there is 6.5 years of my life on those drives...
please help!

##########
[COLOR="DarkRed"]my fdisk -l[/COLOR] 

root@srv1:/etc/3dm2# fdisk -l 

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009f50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030d72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1356

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20202020

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084e19

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       19426   156039313+  8e  Linux LVM
/dev/sde2           19427       19457      249007+   5  Extended
/dev/sde5           19427       19457      248976   83  Linux

############################################
[COLOR="DarkRed"]my   /etc/mdadm/mdadm.conf[/COLOR]

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
MAILADDR [email]xxx@xxx.net[/email]

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=fe6a37fb:c08db5af:385056d0:3e2cf078
devices=/dev/sda,/dev/sdb,/dev/sdc,/dev/sdd


# This file was auto-generated on Tue, 04 Aug 2009 16:19:52 -0700
# by mkconf $Id$

###############
[COLOR="DarkRed"]my mdadm -D /dev/hd0 [/COLOR]


mdadm: Unknown keyword devices=/dev/sda,/dev/sdb,/dev/sdc,/dev/sdd
mdadm: cannot open /dev/hd0: No such file or directory

---

### Post by xtianF on 2011-09-02
its fixed thanks everybody!

---

### Post by benji791 on 2011-09-04
Hello,

Could you please give more details ? I've got the same motherboard. My raid is failed and can't be rebuilt. Could please explain what you've done.

Thanks in advance. Most of my life and wife's life on those drive.

---

