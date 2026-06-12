---
title: "Cannot mount partition - No object for D-Bus interface"
date: 2012-06-24
forum: General Help
---

### Post by Qahne on 2012-06-24
Hey guys, I've recently reformatted a hard drive and Ubuntu fails to mount it. I can't find an info on this anywhere, and I need some help... I've tried deleting it in GParted, I even rebuilt the partition table, it still tells me I can't mount it - "No object for D-Bus interface"

---

### Post by cyrus_the_virus on 2012-06-24
Hi,

Take a look at this solution: [https://bbs.archlinux.org/viewtopic.php?id=140456]("https://bbs.archlinux.org/viewtopic.php?id=140456")

---

### Post by Qahne on 2012-06-24
Thanks for that, the reboot fixed my problem! But now I'm having issues with GNU DDRescue - I entered this on the Live CD:

ubuntu@ubuntu:~$ ddrescue -f /run/media/ubuntu/Acer /run/media/ubuntu/6B10814771260895/back.img  /run/media/ubuntu/6B10814771260895/LOG.TXT


GNU ddrescue 1.16
Press Ctrl-C to interrupt
rescued:         0 B,  errsize:    8192 B,  current rate:        0 B/s
   ipos:      7168 B,   errors:       1,    average rate:        0 B/s
   opos:      7168 B,     time since last successful read:       1 s
Finished                   

...the partition I'm trying to use DD rescue on is 480 GB in size...I cannot figure out where I'm going wrong! I tried unmounting the input partition, but then I had no idea where to find it. Again, I'm such a newb at this...any help, please? Sorry to be a bother : s

---

### Post by gacb on 2012-09-10
I have the same problem with my 64 bit Quantal partition. It doesn't happen on every reboot, but it's annoying when it does.

---

