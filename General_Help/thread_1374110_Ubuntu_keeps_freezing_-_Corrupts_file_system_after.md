---
title: "Ubuntu keeps freezing - Corrupts file system after hard shutdown"
date: 2010-01-06
forum: General Help
---

### Post by phDaemon on 2010-01-06
Ok, this just started happening with ubuntu 9.10.

When it first happened, I didnt know what to do so i accessed all my data, backed it up in a diff partition, reformated my drives and reinstalled a clean 9.10. But now, every now and then (i think its when i use frostwire and have other programs running) my ubuntu keeps freezing up, it becomes non-responsive to anything i do, so i have to do a hard shutdown, after which, when i reboot, it is not able to mount /home, so i run FSCK and it fixes it, but ive done this about 3 times now, its starting to get a bit annoying, i dont know if anyone else has this problem, or if its a known bug. Here are my specs:

Running: Ubuntu Karmic 9.10 64 bit
3 Sata HDD: 1 TB, 750 GB, 350 GB
4GB Ram
2 Nvidia 7900GS
with a Pentium core 2 duo @ 3.0GHz

If any other info is required to advice, please let me know. I consider myself somewhat linux savvy but im stomped on this one.

Thank you.

---

### Post by MooPi on 2010-01-06
Set you system monitor running in the same window as Frostwire and see if it spikes just before a freeze. I use htop , you could use the standard monitor in gnome. recently trying to rip a DVD a similar problem happened. My memory usage spiked and my swap became fully utilized and locked my machine. Just a possible check to see which is the offending application.

---

### Post by phDaemon on 2010-01-06
Good idea, i will do as adviced. BTW, i have 10GB swap partition, (i know its a lot but since i got so much HDD space i figured why the hell not) so if its Frostwire taking up all my ram and swap, there must be a problem in the programming.

Will post back and see if its causing it.

---

### Post by mdmarmer on 2010-01-06
Try to avoid a hard shutdown -- see here:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Mike

---

### Post by phDaemon on 2010-01-06
Very good info. Thank you. Still trying to resolve what is causing these freezes.

---

### Post by wkulecz on 2010-01-06
I've had random hard lockups in Ubuntu before.  Didn't seem to really matter if I booted 6.06 or 8.04.  Swapped in a new power supply and the issue has gone away (system was always on a a UPS).

I can still crash 9.10 to a automatic reboot if I insert a Centon USB MP3 player/memory device.  The Centon device is defective (I've tried three, corrupts data transferd to/from it on W2K, XP, & Win7RC1) but it only spontaneously ejects on 8.04.  This is one of those USB devices that creates a bogus CDROM device, I suspect this is the root of the problem.

If its not specific to doing some repatable action in a single program, its probably a hardware not software issue in my experience.

Booting to the memory test and letting it run as long as practical can't hurt.

--wally.

---

