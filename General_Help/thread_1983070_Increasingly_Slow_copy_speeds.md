---
title: "Increasingly Slow copy speeds"
date: 2012-05-19
forum: General Help
---

### Post by aflyingturtle on 2012-05-19
So recently, I had an iMac computer which for some reason wouldn't boot up and seemed to have errors in the software or something of that nature. So I created a USB drive with 64 bit Ubuntu 12.04 to try and backup the files before I wiped the iMac's drive. The USB stick loaded fine, and I used the 'try ubuntu without installing' option in grub. To start up nautilus so it could access the iMac's hard drive, I ran ```
gksudo nautilus
``` and I began using nautilus to copy the iMac's hard drive over USB 2.0 to an external hard drive I had. At first, the copying was fairly quick, transferring about 7 MB/sec. But as time went on the copying speed steadily dropped, and went down to as low as 500 KB/sec. Any ideas why it would end up so slow?

Edit: By the way, the iMac's hard drive is partitioned as a GUID Partitioning table using the filesystem HFS+ and the external hard drive is partitioned as a Master Boot Record using NTFS.

---

### Post by rai4shu2 on 2012-05-19
That phenomenon is called write-caching. There are two different mechanisms at work, there: the Linux cache (on the software side) and the on-drive cache (on the external hard drive). Once those start flushing, your write speeds go down and down until they flatten out. This is normal.

---

### Post by aflyingturtle on 2012-05-19
> **rai4shu2 said:**
> That phenomenon is called write-caching. There are two different mechanisms at work, there: the Linux cache (on the software side) and the on-drive cache (on the external hard drive). Once those start flushing, your write speeds go down and down until they flatten out. This is normal.
Thanks! I'll just leave it to copy for a while and see if it goes back to normal.

---

