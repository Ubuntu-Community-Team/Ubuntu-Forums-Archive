---
title: "mdadm will not assemble - UUID and superblock problems"
date: 2012-04-21
forum: General Help
---

### Post by chriswthomas on 2012-04-21
Earlier this week the RAID5 array on my little Ubuntu based NAS server went offline.

Investigation showed that there were no apparent or obvious problems on the 5 hard drives which make up the array - all disks are present and accounted for.

It would appear that of the 5 disks, 3 of them have a valid UUID for the array - 2 do not.

I have tried to assemble the array by hand and get:

[FONT=Courier New]chris@NAS1:/etc/mdadm$ sudo mdadm --assemble --scan --verbose --force
mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sdf1
mdadm: /dev/sdf1 has wrong raid level.
mdadm: /dev/sdf is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sde is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: no RAID superblock on /dev/sdd1
mdadm: /dev/sdd1 has wrong raid level.
mdadm: /dev/sdd is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sdc is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sdb5 is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sdb3 is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sdb2 is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sdb1 is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sdb is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sda is not one of /dev/sdc1,/dev/sda1,/dev/sdd1,/dev/sde1,/dev/sdf1
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 4.
mdadm: added /dev/sde1 to /dev/md0 as 1
mdadm: no uptodate device for slot 2 of /dev/md0
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sda1 to /dev/md0 as 4
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 3 drives - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sdf1
mdadm: no recogniseable superblock on /dev/sdf
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdd1
mdadm: no recogniseable superblock on /dev/sdd
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb5: Device or resource busy
mdadm: cannot open device /dev/sdb3: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdb2
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy[/FONT]

The mdadm.conf file lists the 5 devices specifically - /dev/sda1, /dev/sdc1, /dev/sdd1, /dev/sde1 and /dev/sdf1 as two of the drives (e and f) are missing a UUID,

Examining the contents of /dev/sdc1 gives:

[FONT=Courier New]chris@NAS1:/etc/mdadm$ sudo dumpe2fs /dev/sdc1
dumpe2fs 1.41.11 (14-Mar-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          3dd37ec2-5013-4d37-810f-fd86c8d11515
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              244129792
Block count:              976499904
Reserved block count:     48819269
Free blocks:              190274951
Free inodes:              244036763
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      791
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              16
RAID stripe width:        32
Filesystem created:       Mon Sep 13 22:41:47 2010
Last mount time:          Thu Jan 12 19:45:00 2012
Last write time:          Thu Jan 12 19:45:00 2012
Mount count:              4
Maximum mount count:      25
Last checked:             Wed Nov 30 12:59:32 2011
Check interval:           15552000 (6 months)
Next check after:         Mon May 28 13:59:32 2012
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      865735e3-47e6-47d8-90a8-1f88c32fb2f4
Journal backup:           inode blocks
dumpe2fs: Invalid argument while reading journal super block[/FONT]

All of the other devices give the following - even those with a UUID:

[FONT=Courier New]chris@NAS1:/etc/mdadm$ sudo dumpe2fs /dev/sdd1
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdd1
Couldn't find valid filesystem superblock.[/FONT]

I've done lots of Googling and searching but most of the other problems relating to mdadm arrays and superblocks assume you can at least get the array to reassemble by hand and then rely on some form of fsck to resolve the problem... I'm not actually able to get the array to mount.

I have a backup of the important data from some months ago - so not all lost but would obviously like to recover if possible.

Thoughts and suggestions appreciated,

Chris

---

