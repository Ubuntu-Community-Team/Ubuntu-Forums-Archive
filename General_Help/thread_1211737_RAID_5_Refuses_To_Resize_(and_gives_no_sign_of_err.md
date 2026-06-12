---
title: "RAID 5 Refuses To Resize (and gives no sign of errors)"
date: 2009-07-13
forum: General Help
---

### Post by driftfox on 2009-07-13
I created a RAID 5 with 3 1TB WD hard drives. All was well. Until I filled them up. So I purchased one more 1TB WD hard drive. Well it was a D series instead of a C, so when I went to add it, I got an error message about the partition being too small. Come to find out, the D series only has 1953520065 sectors while the C series has 1953525105. Well my plan was to resize the file system, resize (shrink) the array, add the drive, then grow the array followed by the file system. I even tested this theory and was successful on a test RAID 5 array (introducing to it a partition too small, shrinking the array, successfully adding the new partition, then growing the drive).

My problem is that when I run the command to shrink the RAID:

```
mdadm /dev/md0 --grow -z 2925287296
```

it immediately goes back to the command prompt without giving me any error messages, nor showing that it actually did anything. So when I run:

```
mdadm -D /dev/md0
```

I find out that the size of the RAID 5 is STILL set to 2930287296. What could be the cause of this?

Here's some info on my RAID 5:

```

/dev/md0:
        Version : 00.90
  Creation Time : Sat Jul  4 00:28:37 2009
     Raid Level : raid5
     Array Size : 2930287296 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976762432 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 12 23:02:15 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e653bbd8:281dc28b:ba594da2:e359c166
         Events : 0.667116

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       0        0        3      removed

```

(The reason it shows that I have one drive removed is because in my attempts to add the 4th drive for the first time, I accidentally added /dev/sdc instead of /dev/sdc1, which it allowed me to do, but when I realized my mistake, I failed and removed /dev/sdc).

---

### Post by driftfox on 2009-07-13
Is there anything wrong with adding the device (/dev/sdc) to my RAID instead of adding a partition on the device (/dev/sdc1)?

---

### Post by saralee on 2009-11-06
to resize the RAID array there is a detailed guide: 
 
[http://www.partition-tool.com/resource/partition-raid-5.htm](http://www.partition-tool.com/resource/partition-raid-5.htm)

---

