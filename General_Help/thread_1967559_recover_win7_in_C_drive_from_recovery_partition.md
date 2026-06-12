---
title: "recover win7 in C drive from recovery partition"
date: 2012-04-28
forum: General Help
---

### Post by oceanid on 2012-04-28
Dear all
I have a sony vaio vpccw 1vfxu, it had win7 on its 320GB HDD.
I resized partition, removed win7, installed xp on 50BG of my hdd and  installed ubuntu 9.1 on 200GB and a ntfs drive remained for my other data.
in the grub menu I could see linux kernel, memory test, vista loader on /dev/sda1 and xp on /dev/sda2.
now I want to recover my win7 on my C drive. so I select the vista loader but the only things that happens is a "GRUB" word on the top-left corner of screen and pointer blinking .
using f10 the same thing happens.
I have recover DVD for my win7 , when using recover C dirve I get this error: "the C dirve is too small or not exist."
the root of linux is on dev/sda7.
I saw this page [http://ubuntuforums.org/showthread.php?t=1966864&highlight=dual+boot+recovery+partition](http://ubuntuforums.org/showthread.php?t=1966864&highlight=dual+boot+recovery+partition) but could not resolve my problem.

I did reset the bios by f2 then f9 then f10. but the problem not resolved yet.

please note that I don't want to do complete recovery.
also in xp disk manager I saw that the recovery partition is named and 10GB and healthy.

can anyone help me to recover win7 on C drive?
thank you.

---

### Post by oldfred on 2012-04-28
Windows recovery is just an image of hard drive as purchased. I would expect it to want the drive partitioned just like it was as purchased or erased so it can use entire drive.

In hindsight.
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by oceanid on 2012-05-05
you are right,
but as I said before, I have checked that recovery partition is healthy and I did not remove any of its file.
I think that the grub menu not set properly and I want to correct it so that I can recover my system on C partition.

---

### Post by oldfred on 2012-05-05
If just reinstalling Windows 7, you have to erase the Linux partitions from the drive. Windows does not see the Linux partitions but knows the space is used. It wants to install to unallocated space or the NTFS formated partition with the boot flag.

When you install Windows 7 it defaults to two partitions. The first is a small 100MB boot/repair partition, so boot is separate from main install or c: drive. That is just for those who want to encrypt the main install and possibly to have a repair tool outside of the main install. If you create one NTFS partition with the boot flag, it will install to one partition.

---

