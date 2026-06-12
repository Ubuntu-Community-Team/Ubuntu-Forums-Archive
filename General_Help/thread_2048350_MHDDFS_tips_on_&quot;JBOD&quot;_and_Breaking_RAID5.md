---
title: "MHDDFS tips on &quot;JBOD&quot; and Breaking RAID5"
date: 2012-08-26
forum: General Help
---

### Post by chj-se on 2012-08-26
I need some comments in regars to my NAS. I have a Linux Server running Ubuntu 10.04 (may upgrade) and I have a RAID5 for my storage aray, it consits of 4 x 1.5 TB HDDs. OS is running on a seperate disk and I have a 1 TB USB drive that is currently empty.

I am thinking of "destroying" the RAID 5, to gain additional storage space, and start using MHDDFS to mount multiple drives too one mount point for a "large array". Today I loose 1 x 1.5 TB diskspace the the RAID 5. I do not want to run 1 large volume, because if I lose 1 disk, I lose it all.

Any comments in regards to using MHDDFS? I have never tried it before.

Also, any comments in regards to breaking a raid5 using that is setup with MDADM.

**My plan is to:**
1. Move 1 TB of data off the 4 TB raid 5
2. Remove 1 of the drives from the RAID5
3. Format the "broken" drive
4. Move 1.5 TB off the degraded RAID5
5. Reshape the RAID5 with 3 drives
6. Remove 1 of the drives from the "new" RAID5
7. Format the 2nd "broken" drive
8. Move 1.5 TB off the new degraded RAID5, which should be empty
9. Format the remaining 2 drives
10. Mount all drives using MHDDFS

**Questions:**
A. Is my plan viable (assumbing that I have enough data space available)
B. Am I risking all the data by breaking the drives (assuming no HW failures)
C. Comments in regards to MHDDFS
D. Can I mount multiple drives, with data, using MHDDFS to one mountpoint?

Any views and comments?

BTW: I do know that I will not have any redundancy any more, but the main point is not to lose ALL data if A SINGLE drive fails.

Thanks.

---

### Post by chj-se on 2012-09-09
Ok, I solved the issue. Thanks to even more googeling, and a failed drive that "forced" me into moving on with this.

What solved it? Installing an experimental version of mdadm, allows the removal of a drive.

***NOTE:*** This is an **experimental **case, so please do not run if **_you are not willing to risk data_**.

**Links:**
[Blog Post with Howto]("http://blog.stalkr.net/2009/10/reducing-number-of-devices-in-raid-5.html")
[Ubuntu forum post about upgrading]("http://ubuntuforums.org/showthread.php?t=1395450")
[Debian Package for mdadm]("http://packages.debian.org/unstable/admin/mdadm")
[How to Resize RAID]("http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid-p2") (tips only)

**Here is my "solution":**
1. 4 Drives in RAID5, 1 drive failed
```
cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sdd1[3] sde1[2]
      4152360960 blocks level 5, 64k chunk, algorithm 2 [4/3] [U_UU]

mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Apr  8 12:39:06 2011
     Raid Level : raid5
     Array Size : 4152360960 (3960.00 GiB 4252.02 GB)
  Used Dev Size : 1384120320 (1320.00 GiB 1417.34 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  9 11:34:27 2012
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 3ce16aed:03b66e97:272fb3ce:18a82fda
         Events : 0.310190

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1
       3       8       49        3      active sync   /dev/sdd1
```

2. Forced 3 of 4 drives online
```
mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sde1 /dev/sdd1

```

3. Copied out data leaving only 1.3 TB on degraded RAID5

4. Resized /dev/md0 to 1.3TB instead of 4 TB
```
e2fsck -f /dev/md0
resize2fs /dev/md0 1300GB
```

5. Installed mdadm experimental

```

# wget http://ftp.se.debian.org/debian/pool/main/m/mdadm/mdadm_3.2.5-3_i386.deb

#dpkg -i mdadm_3.2.5-3_i386.deb

# mdadm --version
mdadm - v3.2.5 - 18th May 2012

```

6. Resize Array
```
# mdadm /dev/md0 --grow --array-size=1385120320

# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Apr  8 12:39:06 2011
     Raid Level : raid5
     Array Size : 1385120320 (1320.95 GiB 1418.36 GB)
  Used Dev Size : 1384120320 (1320.00 GiB 1417.34 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  9 12:46:27 2012
          State : clean, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 3ce16aed:03b66e97:272fb3ce:18a82fda
         Events : 0.310204

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1
       3       8       49        3      active sync   /dev/sdd1

```

7. Decrease number of drives
```
# mdadm /dev/md0 --grow  --raid-devices=3 --backup-file=/tmp/mdadm.backup
mdadm: Need to backup 384K of critical section..
```

8. View new raid set
```
# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.91
  Creation Time : Fri Apr  8 12:39:06 2011
     Raid Level : raid5
     Array Size : 1385120320 (1320.95 GiB 1418.36 GB)
  Used Dev Size : 1384120320 (1320.00 GiB 1417.34 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  9 14:03:55 2012
          State : clean, degraded, reshaping
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Reshape Status : 0% complete
  Delta Devices : -1, (4->3)

           UUID : 3ce16aed:03b66e97:272fb3ce:18a82fda
         Events : 0.310214

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1

       3       8       49        3      active sync   /dev/sdd1
```

8. Monitor progress
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[0] sdd1[3] sde1[2]
      1385120320 blocks super 0.91 level 5, 64k chunk, algorithm 2 [3/2] [U_U]
      [>....................]  reshape =  0.0% (476800/1384120320) finish=3005.5min speed=7672K/sec

```

Now I just need to wait for 50 hours for the reshape to be done! Data is accessable still, so lets hope that nothing kills the data on the drive.

---

