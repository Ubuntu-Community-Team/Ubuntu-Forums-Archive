---
title: "RAID1 array fails on reboot - advice?"
date: 2010-09-08
forum: General Help
---

### Post by creativelies on 2010-09-08
I did a search and couldn't find anything pertaining to this - if I've missed something please direct me in the right direction :)

We have an Ubuntu box set up as a headless office server (latest desktop install of Ubuntu) and we recently set up two 1TB HDDs in a RAID1 array using mdadm - as far as I can tell it worked successfully and created /dev/md0 with an ext3 file system.  After sharing the drive I can see it from the other office computers and could transfer data to and from the RAID array just fine.

I didn't figure out how to get it to automatically mount on boot so I restarted it to see if it would do so by default - however, when I restarted I couldn't see the RAID array any longer on the desktop and it came up as a 0.0kb RAID array in Disk Utility, saying it was broken.  It wouldn't let me check it until I stopped and restarted the array.

After restarting I hit "check array" and it appears to be repairing the drives.

What have I missed?  What happened here?  How can I fix it?  What other info can I provide to assist?  If any of this helps:

sudo blkid shows:

/dev/sda1:  UUID: "<snip>" TYPE="ext3" (system HDD)
/dev/sda5: UUID: "<snip>" TYPE="swap"
/dev/sdc1: UUID: "<snip>" TYPE="linux_raid_member"
/dev/sdb1: UUID: "<snip>" TYPE="linux_raid_member"
/dev/md0: UUID: "<snip>" SEC_TYPE="ext2" TYPE="ext3"

disk utility:

RAID Array:  Mirror (RAID-1), Metadata version 0.90.0, Partitioning:  Not Partitioned, Components: 2...

Thanks for any help.

---

### Post by creativelies on 2010-09-09
Solved!

Did some more searching and found this thread:

[http://ubuntuforums.org/showthread.php?t=1513405&highlight=Raid](http://ubuntuforums.org/showthread.php?t=1513405&highlight=Raid)

Followed the directions and it now works A-OK.  Very happy. :D

---

