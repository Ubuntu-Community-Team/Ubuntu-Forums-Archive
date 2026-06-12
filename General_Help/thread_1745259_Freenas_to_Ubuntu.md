---
title: "Freenas to Ubuntu"
date: 2011-04-30
forum: General Help
---

### Post by sbollapa on 2011-04-30
This is my first post on ubuntu and am sorry if this is not the correct forum.
To my question:
I have NAS setup(RAID1) using freenas and was using it for last 2months.
I somehow feels not comfortable for any upgrades for any software in freenas so planning to move to Ubuntu for NAS. 
I took a backup from the freenas (from UI menu). if I move to ubuntu, can i use that backup so that my data on NAS doesn't get affected?
my RAID1 setup is 2TB*2 and it is already 70% full.

---

### Post by tgalati4 on 2011-04-30
The backup only backs up the freenas configuration file, so you can move to another freenas machine, reload the backup configuration file and you are up and running with all of your defined shares, etc.  It works quite well.  As far as data backup, you run some risks.  Freenas uses a different partitioning scheme and a different file system than Ubuntu.

Freenas is not really designed for upgrading.  It's current, stable version is 7.2 and version 8 is a complete rewrite with many features still not working.  So if you installed 7.2 you will be good for many years.  If you are moving from freenas (which is a an excellent NAS) to a full-fledged server (such as Ubuntu server), there is no simple way (that I know of) to move the data without having another 4 TB NAS to hold the data, build the new server, then migrate the NAS-held data to the server.  Any other solution justs puts your data at risk.

I think you are asking: "Can I overwrite freenas with Ubuntu server and keep my 3 TB of data?"

No.

When you built a freenas server, you are committed to that solution.

---

