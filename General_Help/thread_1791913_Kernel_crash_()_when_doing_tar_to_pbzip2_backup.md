---
title: "Kernel crash (?) when doing tar to pbzip2 backup"
date: 2011-06-27
forum: General Help
---

### Post by gearond on 2011-06-27
<Any thoughts on this, or discussions on similar problems VERY Welcome!>

Using Ubuntu 10.10 fully updated on 2 core(4 core?) Intel I5 2.4 ghz.

Doing backups of laptop's internal drive, partition 1, boot partition EXT4, Ubuntu 10.10.

Running Ubuntu externally on target drive in one partition (/dev/sdb1) and target filesystem NTFS (/dev/sdb2).

Command issued in terminal: tar -c /media/SDA1_VOLUME_NAME | pbzip2 > /media/SDB2_VOLUME_NAME/backup.tar.bz2

Getting Kernel panic when doing high load, full backup. If I use pbzip2 to compress a full partition backup on my laptop's hardrive to an external USB disk, after some variable amount of time, I get a non responsive machine, with an image on the screen, and a flashing caps lock key.

My thoughts are:
-----------------
A/ Bad hardrives
B/ Bad CPU
C/ Bad Memory
D/ Bad driver
E/ Bad Ubuntu, pbzip2 somehow?
F/ Tar not liking such big files?


What I've tried:
-----------------
Ran bad blocks on both input and output drives
--nothing found
Ran smartctl on source disk
-- says it's good, but has had some read read/write errors and seek errors sometime in the past. Values are well above thresholds
Ran memtest+ on latop lots of passes overnight
--nothing found

Going to try:
-----------------
cpuburn program.
running only using regular bzip2, with less load.


This whole thing is a PITA, I love my machine and it's a great one from [http://www.m-techlaptops.com/](http://www.m-techlaptops.com/) I'd sure like to know where the problem is.

---

### Post by gearond on 2011-06-27
Now have run the LONG smartctl on the internal hard drive (sudo smartctl -t long /dev/sda) with no big problems showing up.

Running badblocks on the destination device (external USB), and it will take 20 hours for a 450gb drive. I tried upping the number of blocks at a time WAY above the default (16384 vs 64) to try and speed it up, but did not notice any real difference.

Will report on that. The internal drive passed using the standard 'badblocks' settings.

After that, it's CPU burn. and trying the same thing on another machine, using all different equipment, but the same ubuntu 10.10 installed on a different external drive.

---

