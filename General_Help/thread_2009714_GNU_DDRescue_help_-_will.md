---
title: "GNU DDRescue help - will"
date: 2012-06-24
forum: General Help
---

### Post by Qahne on 2012-06-24
Hey guys, my HDD recently crashed, and Windows will no longer boot. I'm trying to use GNU ddrescue to retrieve some of my files from there, so I entered this on the Live CD:

ubuntu@ubuntu:~$ ddrescue -f /run/media/ubuntu/Acer /run/media/ubuntu/6B10814771260895/back.img /run/media/ubuntu/6B10814771260895/LOG.TXT


GNU ddrescue 1.16
Press Ctrl-C to interrupt
rescued: 0 B, errsize: 8192 B, current rate: 0 B/s
ipos: 7168 B, errors: 1, average rate: 0 B/s
opos: 7168 B, time since last successful read: 1 s
Finished 

...the partition I'm trying to use DD rescue on is 480 GB in size...I cannot figure out where I'm going wrong! The partition I'm trying to read from mounts fine in Ubuntu, and I can see the folders within just fine. I tried unmounting the input partition, but then I had no idea where to find it. I'm such a newb at this...any help, please? Sorry to be a bother : s

---

### Post by raja.genupula on 2012-06-24
Hi follow this link , its having best things for data recovery 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Qahne on 2012-06-24
Thanks, but I've already read that a few times. Maybe I wasn't clear enough the first time...my question is, do I have to install Ubuntu for DD Rescue to view the partitions properly?

---

### Post by raja.genupula on 2012-06-24
No , No Need to install Ubuntu amigo . A live session will be enough . If you want to recovery the data i suggest you too go through the** testdisk** .

---

