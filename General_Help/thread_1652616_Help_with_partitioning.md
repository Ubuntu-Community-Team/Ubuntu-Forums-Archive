---
title: "Help with partitioning"
date: 2010-12-25
forum: General Help
---

### Post by alexthunder on 2010-12-25
I have partitioned my hd204ui using the following tutorial
[http://stream-recorder.com/forum/partition-samsung-hd204ui-ubuntu-linux-hdd-w-t8032.html](http://stream-recorder.com/forum/partition-samsung-hd204ui-ubuntu-linux-hdd-w-t8032.html)

Basically I was using fdisk for partitioning, since I thought Gparted wouldn't handle advanced format properly. I created 2 partitions, making sure the first cylinder is a multiple of 8. 

I have 2 problems though:
1. the test showed speed of 100-140 MB/s, but in reality I only see 25-35  MB/s.
2. although I formated one of my partitions to NTFS, I can't see it in Windows 7.

What was wrong in my steps?

---

### Post by bodhi.zazen on 2010-12-25
I moved your post to a support section. Tips & tutorials is not for support, lol.

I am not sure about the speed, what test did you run ? read and write speed are not the same thing, we need more details. If you are referring to speed test on the tutorial you found, your speed tests will not be the same unless you have the same hardware.

As far as windows goes, again you did not provide much in the ways of details.

Can Ubuntu (Linux) see both partitions ? On flash drives Windows can often see only one partition, the first one, so put the ntfs partition first.

---

### Post by alexthunder on 2010-12-29
My speed tests:

username@computername:~$ sudo hdparm -i /dev/sdb | grep Model
 Model=SAMSUNG HD204UI, FwRev=1AQ10003, SerialNo=S2H7J9CZB05820

username@computername:~$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:  412 MB in  3.01 seconds = 136.74 MB/sec
Code:
username@computername:~$ sudo dd if=/dev/sdb of=/dev/null bs=128K count=20000
20000+0 records in
20000+0 records out
2621440000 bytes (2.6 GB) copied, 17.4932 s, 150 MB/s

username@computername:~$ sudo dd if=/dev/zero of=/dev/sdb bs=128K count=20000
20000+0 records in
20000+0 records out
2621440000 bytes (2.6 GB) copied, 18.2465 s, 144 MB/s

username@computername:~$ dd if=/dev/zero of=/media/ext4/000.dd bs=128K count=100000
100000+0 records in
100000+0 records out
13107200000 bytes (13 GB) copied, 128.477 s, 102 MB/s


Ubuntu doesn't have any problem with both partitions. It is only Windows 7 that can't see it on my Samsung HDD.

---

### Post by alexthunder on 2010-12-29
Apparently the tutorial [here](http://stream-recorder.com/forum/partition-samsung-hd204ui-ubuntu-linux-hdd-w-t8032.html) was updated. It works fine for me now. Just made sure the first sector of each partition was a multiple of 64.

---

