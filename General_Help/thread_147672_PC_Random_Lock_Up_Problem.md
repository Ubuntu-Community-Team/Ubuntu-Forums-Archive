---
title: "PC Random Lock Up Problem"
date: 2006-03-20
forum: General Help
---

### Post by Phlosten on 2006-03-20
Hi all,

I am getting this strange problem with my PC 'locking' up every now and then, but it isnt a full lock-up, I just find that I cannot open any programs etc. Whatever is open seems to work but anything the accesses the hard disk refuses to work. Its like the filesystem locks up.

I had previously thought I may have had some messed up partitions, but I have since cleared everything and completely reinstalled everything fresh and neat. Since then (about 1 week ago) I havent experienced the issue until last night when I was ripping a DVD. The program crashed and I could not open anything or restart X, I could only turn the PC off. (If I pressed the reset button to hard reboot I found that the BIOS was not detecting the disks. I had to actually remove power to restart).

At first I thought it could be a dodgy hard disk which is a brand new seagate baracuda 80GB, or possibly my RAM was faulty, 512M), but I have run a check on the hard disk and 12 memory test passes on the ram (all night), and everything seems fine there.

There are errors in the kern.log, and here they are.

> Mar 20 22:04:45 localhost kernel: [  177.643407] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Mar 20 22:04:45 localhost kernel: [  177.643417] hdc: command error: error=0x50 { LastFailedSense=0x05 }
Mar 20 22:04:45 localhost kernel: [  177.643422] ide: failed opcode was: unknown
Mar 20 22:04:45 localhost kernel: [  177.643428] end_request: I/O error, dev hdc, sector 256
Mar 20 22:04:45 localhost kernel: [  177.643433] Buffer I/O error on device hdc, logical block 64
Mar 20 22:04:45 localhost kernel: [  177.643438] lost page write due to I/O error on hdc
Mar 20 22:57:05 localhost kernel: [ 3317.720742] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Mar 20 22:57:05 localhost kernel: [ 3317.720752] hdc: command error: error=0x50 { LastFailedSense=0x05 }
Mar 20 22:57:05 localhost kernel: [ 3317.720756] ide: failed opcode was: unknown
Mar 20 22:57:05 localhost kernel: [ 3317.720763] end_request: I/O error, dev hdc, sector 256
Mar 20 22:57:05 localhost kernel: [ 3317.720769] Buffer I/O error on device hdc, logical block 64
Mar 20 22:57:05 localhost kernel: [ 3317.720774] lost page write due to I/O error on hdc

These errors seem to point towards to my dvd drive. This is a brand new LG dvd drive, and I was experiencing these errors with 2 other different cd drives installed.

Can anyone offer some suggestions of what may be wrong? Has anyone experienced similar issues? I fear it is hardware related but I don't know whether there is much more to test.

As to my hardware, I have:
AMD Athlon XP 2000+
MSI all-in-one mainboard (savage on-board graphics sharing 32MB ram and network card in use, sound card disabled)
512MB Ram
Seagate Barracuda 80GB IDE drive
LG DVD Writer

Any help would be much appreciated. Maybe someone can point me towards some good (free) testing tools?

---

### Post by centyx on 2007-05-19
Did you ever find a solution to this problem? I am experiencing the same errors, but during an Ubuntu alternate CD install. The install locks up and is unable to proceed.

---

### Post by centyx on 2007-09-12
In my case, the problem was a faulty cdrom drive.

---

