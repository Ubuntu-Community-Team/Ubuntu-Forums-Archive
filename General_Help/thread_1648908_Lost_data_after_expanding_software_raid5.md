---
title: "Lost data after expanding software raid5"
date: 2010-12-19
forum: General Help
---

### Post by Reinkens on 2010-12-19
Hello,

I was able to add a 4th disk to my software raid5. However, after mounting the raid, my files and folders no longer appear, only a "lost+found" folder. Am I SOL or is there a way or undoing the changes or recovering the files?

I initially had 3 drives in the array /dev/sd[fgh] using ext4. Here are the commands I ran to expand the array with /dev/sdi.
```
sudo umount /dev/md0
sudo mdadm --add /dev/md0 /dev/sdi
sudo mdadm --grow /dev/md0 --raid-devices=4

cat /proc/mdstat
# waited for it to complete (~12 hours)

sudo e2fsck -f /dev/md0
sudo resize2fs /dev/md0

cat /proc/mdstat
# waited for it to complete (~6 hours)

sudo mount -t ext4 /dev/md0 /media/raid
```

The volume and ext4 filesytem has increased correctly (2TB -> 3TB). Here is the raid details
```
sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue Oct 28 22:16:55 2008
     Raid Level : raid5
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Dec 19 09:21:23 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 006a6556:cc72c806:e623d503:1e8b047e
         Events : 0.282887

    Number   Major   Minor   RaidDevice State
       0       8       80        0      active sync   /dev/sdf
       1       8      112        1      active sync   /dev/sdh
       2       8       96        2      active sync   /dev/sdg
       3       8      128        3      active sync   /dev/sdi
```
-Reinkens

---

