---
title: "Raid 1 rebuild question"
date: 2011-05-29
forum: General Help
---

### Post by creativelies on 2011-05-29
Hello all.

I have two old 80GB HDDs that are part of the computer's 60GB RAID1 system partition.  I have two newer, quieter and faster 250GB HDDs that I would like to replace them with. The RAID1 partition was created during the Ubuntu 11.04 Server install.

I have one spare SATA port so my plan was to take one of the 80GB drives offline, install the two 250GB drives, add them to the md0 array to make it a three-disc RAID1 array and then remove the remaining 80GB drive via Disk Utility (needed a GUI on the server after all so there's some regular desktop programs on there now).

I've removed the 80GB, added in the 250GB drives and added them into the md0 array using Disk Utility, and now the relevant output of fdisk -l is:


[quote="fdisk -l"]Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9328    74920960   fd  Linux RAID autodetect
/dev/sdb2            9328        9730     3227649    5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris



Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00037968

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9327    74919096   fd  Linux RAID autodetect



Disk /dev/sdg: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000815ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        9327    74919096   fd  Linux RAID autodetect


Disk /dev/md0: 60.0 GB, 60020424704 bytes
2 heads, 4 sectors/track, 14653424 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table[/quote]

and mdstat:

[quote="mdstat"]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdf1[1] sdc1[0]
      976762432 blocks [2/2] [UU]
      
md2 : active raid1 sda1[1] sde1[0]
      1953514414 blocks super 1.2 [2/2] [UU]
      
[B]md0 : active raid1 sdb1[0] sdd1[1] sdg1[2]
      58613696 blocks [3/3] [UUU][/B][/quote]


also fstab, if that helps:

[quote="fstab"]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=ef4c8184-821f-4c0c-9af6-a95be315f3f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=4de3a274-6ab6-4ad3-8bd8-d93c5795515c none            swap    sw              0       0
[/quote]



My main question is - why aren't the partitions the same across the new drives that have been added in?  I'm worried that if I pull the original 80GB the system won't function properly since I haven't rebuilt the RAID array in the correct fashion. We need this computer online as much as possible since it's a file server for photos/videos and so I don't want to chance pulling the other 80GB drive and breaking something.

If I pull the 80GB, am I left with no swap partition?

Any help or links appreciated!  I couldn't find anything relevant through searching...

---

