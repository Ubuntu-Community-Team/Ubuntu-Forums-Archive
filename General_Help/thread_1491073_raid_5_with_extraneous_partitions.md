---
title: "raid 5 with extraneous partitions"
date: 2010-05-23
forum: General Help
---

### Post by derek71 on 2010-05-23
I recently installed Ubuntu 10.04 server to act as a NAS and created a RAID 5 using mdadm.

I have been successful in building the array: mdadm reports that the array is clean and the superblock is persistent.

After I formatted the RAID with NTFS (in order to preserve Windows files attributes), I checked fdisk again and noticed two messages that I am concerned with:

After listing the RAID device /dev/md0, there is a message. "This doesn't look like a partition table.  Probably you selected the wrong device".

Following this message are four partition definitions of the form: /dev/md0p1.  The four partitions have different filesystems and the start/end locations appear to be overlapping.  

These were created somehow during the array generation.

The RAID seems operational though I would like to find out what these messages mean.

---

