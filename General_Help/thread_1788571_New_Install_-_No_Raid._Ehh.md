---
title: "New Install - No Raid. Ehh???"
date: 2011-06-22
forum: General Help
---

### Post by Roasted on 2011-06-22
250gb SATA - Windows 7 + Ubuntu 11.04
1TB SATA - Software Raid 1 (mounted to home directory)
1TB SATA - Software Raid 1 (mounted to home directory)

I reinstalled Ubuntu 11.04 and did a manual partition, leaving my raid array entirely alone. Now that I'm done installing, I get:

jason@Area51:~$ cat /proc/mdstat 
Personalities : 
unused devices: <none>
jason@Area51:~$ 



jason@Area51:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e944f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       26134   209817600    7  HPFS/NTFS
/dev/sda3           26134       26864     5859328   82  Linux swap / Solaris
/dev/sda4           26864       30516    29336576   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032106

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976760832   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012999

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832   fd  Linux raid autodetect
jason@Area51:~$ 



I know how to edit fstab once I figure out how to get /dev/md0 back up and running, but how do I fix my current issue so my array can at least be seen??



EDIT - Seems as if I just had to apt-get install mdadm... then reboot... now I see:

jason@Area51:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0] sdc1[1]
      976759672 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
jason@Area51:~$ 


Well, my mistake. Lesson learned! Hoping someone else can learn by this post...

---

