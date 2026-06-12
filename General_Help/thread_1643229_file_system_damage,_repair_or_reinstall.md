---
title: "file system damage, repair or reinstall?"
date: 2010-12-11
forum: General Help
---

### Post by philkahly8 on 2010-12-11
I booted up Ubuntu after a couple weeks of downtime. I think it had just installed updates before I shut it down. It seemed fine. I started updating it, then it started giving me a bunch of errors about the root file system being mounted read only, so I had to reboot. I've heard that it does that if the file system is corrupted or there is a hard disk failure. When I rebooted, it kernel panicked on all but the oldest kernel which did a fsck and rebooted. Then I was able to get back in, but most of my panel applets are gone and cannot be restored, it fails to start x at boot with no errors and I have to start it myself from the command line, it is unable to do updates, samba is gone, whenever I update-grub to add Gentoo to the list, it doesn't stay there and the computer is really slow. I have backed up my home folder to another partition. Do you think I will be able to repair it at all or should I just reinstall?

---

### Post by Old_Grey_Wolf on 2010-12-11
Back up you home folder to another storage device and not just another partition on the same storage device. If you have a CD from the computer manufacturer that has diagnostic on it you should run a check of the hard disk. A reinstall may help for a while; however, if the disk is failing it won't help for very long.

---

### Post by philkahly8 on 2010-12-11
Good advice, but I don't have another storage device that can hold near this amount of data. I do have the most important stuff on my flash drive though. I built this computer so I don't have any disks. I will try to find some diagnostic utilities.

---

### Post by Old_Grey_Wolf on 2010-12-11
If you built it yourself then you may be able to find diagnostic software from the disk manufacture, it you don't already have it.

---

### Post by philkahly8 on 2010-12-11
The disk is a Western Digital. I don't have a disk for it and all the  downloads I saw on their site are Windows or Dos. The one is supposed to  make a floppy but I don't have a floppy drive. I've booted from a live  CD and did the tests in the Disk Utility. It says there are 6 bad  sectors. But that it is healthy. The disk is only 6-7 months old.

---

### Post by oldos2er on 2010-12-12
Have you tried running fsck from the LiveCD?

---

### Post by philkahly8 on 2010-12-12
I have ran fsck on all the partitions from Gentoo and the Live CD. There was some repairs when I first ran it from the old kernel in Ubuntu, but all the others say it is clean. Oh, and when I checked to smart data again it said 5 bad sectors instead of 6.

---

### Post by philkahly8 on 2010-12-12
Well, I booted back into Ubuntu and x wouldn't start because the nvidia driver can't be found and I had to delete that line from the configuration file. I guess I'll just format, reinstall and hope that was the problem. I don't suppose it would do any good to make a new partition table? Many thanks to both of you. I'll mark this as solved, but if you have any other suggestions I would be glad to hear them.  Thanks again.

---

### Post by efflandt on 2010-12-12
Normally a hard drive reserves some space to automatically transparently remap good sectors in place of bad sectors behind the scenes.  If you start actually seeing bad sectors, that is usually a bad sign.  It could mean that all the error sites are used up.  If a chunk of something is floating around the spinning platters it can only get worse.

The drive should be under warranty (they can tell from mfr date of serial number if you do not have receipt). But I am not sure the best way to copy Linux data over.

My boss' grandsons crashed a drive on an old WinXP laptop.  At first I could not read that drive at all in Linux or Windows.  But after sitting a few weeks (after reinstalling Windows on a new drive), it auto mounted in Ubuntu in USB enclosure and I was able to get most data from the user's home directory.

Sometime later it would not boot the new drive. From WinXP on another PC, chkdsk /f fixed it enough to boot WinXP (only losing one dll).  I could not get clonezilla on CD to image it (stopped when it got to bad sectors). But WD version of Acronis was able to image it for the warranty replacement drive (default by files instead of sector by sector).  Sometime after that the warranty replacement drive would not boot again, but that turned out to be Windows viruses and I was able to fix that.  Then they gave it to me with a broken screen, so not sure how gentle they were with it (old laptop anyway).

---

