---
title: "RAID 5 device fails to assemble with mdadm!"
date: 2012-09-24
forum: General Help
---

### Post by tehschulman on 2012-09-24
I've got a file server I've been making an effort to recover for a few weeks now. I first noticed some issues with my disks after a blackout that suddenly powered off the server.

Ever since, I've been unable to maintain a stable Ubuntu system. I've been meaning to reformat and reinstall the server for a while, but now with the performance issues I've decided to do this sooner rather than later.

In order to recover my media, I purchased a Network Attached Storage and have been in the process of transfering files over to this backup device. Last night, while transfering some folders, I noticed that the file transfer was having issues with some of the files. Looking closer, I noticed that many of my directories had files that weren't accessible but previously had no issues.

To try and remedy this, I rebooted the system and loaded up the livecd again, but now when I uses mdadm to assemble the two RAID arrays in my server, I get the following message:

```


ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 2 drives and 1 spare.
mdadm: failed to add /dev/sdc3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdb3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sda3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdd3 to /dev/md1: Invalid argument
mdadm: /dev/md1 assembled from -1 drives and 1 spare - not enough to start the array.
mdadm: failed to add /dev/sdc3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdb3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sda3 to /dev/md1: Invalid argument
mdadm: failed to add /dev/sdd3 to /dev/md1: Invalid argument
mdadm: /dev/md1 assembled from -1 drives and 1 spare - not enough to start the array.


```

/dev/md0 contains my system, but /dev/md1 contains my /home directories and the majority of my media files. Now as it stands, I'm unable to mount or activate my media partition which is set up as a RAID 5 array. Examining the disks in the array returns the following:

```



ubuntu@ubuntu:~$ sudo mdadm -E /dev/sda3
/dev/sda3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Mon Sep 24 06:49:19 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Sep 24 06:55:10 2012
          State : active
 Active Devices : 0
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 4
       Checksum : 9ed4a3cd - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     3       8        3        3      spare   /dev/sda3

   0     0       8       51        0      spare   /dev/sdd3
   1     1       8       35        1      spare   /dev/sdc3
   2     2       8       19        2      spare   /dev/sdb3
   3     3       8        3        3      spare   /dev/sda3


ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Mon Sep 24 06:49:19 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Sep 24 06:55:10 2012
          State : active
 Active Devices : 0
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 4
       Checksum : 9ed4a3db - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     2       8       19        2      spare   /dev/sdb3

   0     0       8       51        0      spare   /dev/sdd3
   1     1       8       35        1      spare   /dev/sdc3
   2     2       8       19        2      spare   /dev/sdb3
   3     3       8        3        3      spare   /dev/sda3


ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdc3
/dev/sdc3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Mon Sep 24 06:49:19 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Sep 24 06:55:10 2012
          State : active
 Active Devices : 0
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 4
       Checksum : 9ed4a3e9 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     1       8       35        1      spare   /dev/sdc3

   0     0       8       51        0      spare   /dev/sdd3
   1     1       8       35        1      spare   /dev/sdc3
   2     2       8       19        2      spare   /dev/sdb3
   3     3       8        3        3      spare   /dev/sda3



ubuntu@ubuntu:~$ sudo mdadm -E /dev/sdd3
/dev/sdd3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Mon Sep 24 06:49:19 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Sep 24 06:55:10 2012
          State : active
 Active Devices : 0
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 4
       Checksum : 9ed4a3f7 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8       51        0      spare   /dev/sdd3

   0     0       8       51        0      spare   /dev/sdd3
   1     1       8       35        1      spare   /dev/sdc3
   2     2       8       19        2      spare   /dev/sdb3
   3     3       8        3        3      spare   /dev/sda3

```

The null UUID bothers me. Am I at the point where I need to buy a new disk and rebuild my array? I've done a few RAID setups in my day but this will be my first hardcore RAID rebuild/recovery. Where should I start?

---

### Post by tehschulman on 2012-09-25
Hmm, maybe there is a better place for this thread than General Help. Could a mod please move this thread to the appropriate board? Thank you!

---

