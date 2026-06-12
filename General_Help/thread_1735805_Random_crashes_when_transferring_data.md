---
title: "Random crashes when transferring data"
date: 2011-04-21
forum: General Help
---

### Post by drewbob on 2011-04-21
I set up an old desktop to use as storage with Ubuntu 10.10.  I actually had some problems setting up firstly FreeBSD and then Gentoo, which I was hoping to experiment with.  FreeBSD installed fine but startx insta-crashed it and after a couple of days I couldn't fix it.  Gentoo would freeze when compiling the kernel, but Ubuntu installed fine.

When transferring over the data using SSH over a LAN, after about 10/15 minutes the computer crashes.  Is this a common problem with large transfers over SSH?  Which log files should I look at to try and get some info on the problem? Is there anything in common with startx on FreeBSD, kernel compiling on Gentoo and large transfers on Ubuntu?

Thanks,

Andrew

---

### Post by hwttdz on 2011-04-21
There is something in common, they all use the same hardware.  I'd look at /var/log/messages, errors, dmesg, syslog...

You can try stress testing?  You can also look at the SMART attributes of the hard disk.

---

### Post by drewbob on 2011-04-24
Looked into some stress testing and ran memtest86 or whatever it's called from grub.  Got some fails on test 7, does this just mean my ram is buggered or are there ways to fix it?  I've tried moving it to the other ram slot and I get the same thing.

---

### Post by drewbob on 2011-04-24
Oh and as for the logs there doesn't seem to be anything in there, so it seems that whatever causes the crash stops the logs writing as well, so it really does just die.

---

