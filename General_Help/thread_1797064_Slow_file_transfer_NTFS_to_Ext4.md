---
title: "Slow file transfer: NTFS to Ext4"
date: 2011-07-04
forum: General Help
---

### Post by aoniumo on 2011-07-04
I am trying to move over 1 Terrabyte of files from a two terrabyte drive into my Ext4 drive where Ubuntu 11.04 is installed.  The two terrabyte drive is where my winxp used to be and it's currently paritioned into three partitions. I would like to reformat into a single partition that's why I'm moving the files.

When moving the files from the 2Terrabye NTFS partition into the Ext4 partitioned drive, the best transfer rate I could get is 11 megabytes per second.  When I transfer from one NTFS drive to another NTFS drive, I could get as high as 70megabytes per second in WinXP.  Is there a way to speed up the speed transfer?

Otherwise, the file transfer dialogue says it would take 26 hours to move all the files!!!

Edit: both drives are internal drives connected via a sata II.

---

### Post by wildmanne39 on 2011-07-04
> **aoniumo said:**
> I am trying to move over 1 Terrabyte of files from a two terrabyte drive into my Ext4 drive where Ubuntu 11.04 is installed.  The two terrabyte drive is where my winxp used to be and it's currently paritioned into three partitions. I would like to reformat into a single partition that's why I'm moving the files.

When moving the files from the 2Terrabye NTFS partition into the Ext4 partitioned drive, the best transfer rate I could get is 11 megabytes per second.  When I transfer from one NTFS drive to another NTFS drive, I could get as high as 70megabytes per second in WinXP.  Is there a way to speed up the speed transfer?

Otherwise, the file transfer dialogue says it would take 26 hours to move all the files!!!

Edit: both drives are internal drives connected via a sata II.
Hi, as far as I know  there is no way to speed it up, but maybe someone else has a way and will post it.

---

### Post by aoniumo on 2011-07-04
But why is the transfer rate going only 11MB/sec?

Edit: Also. Even though 11MB/sec is not the optimum transfer rate between drive, ubuntu is acting up like it's too busy.  CPU and memory load is 10% or less, but computer occasionally freezes and I can barely switch between tabs in Firefox without firefox freezing and me waiting a few seconds.

---

### Post by cre8ive65 on 2011-07-04
NTFS file system is most likely corrupt, try going into windows (make sure to hold your nose ;) ) and running chkdsk /F in CMD, that should tidy everything up for you

I had this problem a while back when i tried to resize a partition it would take 3 hours or more!

And by the way, for the love of god, DO NOT interrupt chkdsk /F

---

