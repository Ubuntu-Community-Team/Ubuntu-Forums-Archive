---
title: "Manually edit gpt guid partition"
date: 2009-12-10
forum: General Help
---

### Post by uniden9 on 2009-12-10
I have expanded my dell perc 5i in my media pc from 7499TB to 10500TB. It has only a single partition, a lvm with the lvm option set.  I have successfully expanded the array, but have hit a wall in how to resize the gpt partition table.  Please not I do not want to resize the actual filing system/ lvm pv in the array, just partition table.  The same machine also has another soft raid 5,mdadm, array, which doesn't have any partition table , and has successfully resized it three times, (3 drive->5->6) and the lvm in that's coexists on it. 

My problem is, I'm not sure how to do this with a gpt guid partition table.  Normally I'd just use sfdisk and reset the ending.  But sfdisk does not support gpt. Can I use parted to remove the partition and then re-create the partition over it and set the new larger ending point?  My only concern is, parted doesn't seem to be real specific on starting points. It's not to the sector/block like fdisk or sfdisk, but a arbitrary size.  I'm somewhat concerned that a rounding error would mess up the beginning in recreation.  This would break the lvm, as it couldn't be detected. Also I'm not sure how you backup the gpt partition table of a gpt, again I typically use sfdisk for this.

(parted) print free
Model: DELL PERC 5/i (scsi)
Disk /dev/sdg: 10.5TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  7499GB  7499GB               primary  lvm
        7499GB  10.5TB  2999GB  Free Space

I'm running Ubuntu 9.10 Generic kernel, 64bit. 
8 Seagate 1.5TB raid 5 on perc 5i and 6 Seagate 1.5TB soft raid 5 on internal intel sata controller.

Thanks

---

### Post by uniden9 on 2009-12-11
To answer my own question. This is not possible with parted. Its been on the gnu parted todo features for 3 1/5 years, but hasn't happened.  The gpt partition has crc32's that have to updated for this work, which parted is currently not able to do. Parted will only resize the file system and partition, its unable to leave the file system alone.

[http://www.gnu.org/software/parted/faq.html](http://www.gnu.org/software/parted/faq.html)

Can I resize only the partition, leaving the file system as it is?

Not at this time. This feature is scheduled for 1.7.1 or 1.7.2, however.

---

### Post by srs5694 on 2010-03-08
I realize your post is rather old, but I thought you might be interested to know that my [GPT fdisk](http://www.rodsbooks.com/gdisk/) tool can do what you want. Well, not precisely, but close enough: You can delete an existing partition and create a new one in its place with the (sector-exact) same starting point. If necessary, you can cut-and-paste the original partition's GUID for use by the new one.

---

