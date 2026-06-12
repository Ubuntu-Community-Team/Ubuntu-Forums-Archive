---
title: "NTFS Format &amp; Data Recovery"
date: 2009-11-27
forum: General Help
---

### Post by Yunus Emre on 2009-11-27
Hi.

I've made a mistake and formatted my external HDD instead of my flash drive. I've right-clicked the HDD's desktop shortcut and clicked "Format". As it started formatting I've seen that it's the wrong drive and plugged out USB cable.

Here's the question, how far can it be gone? Is it possible that Ubuntu has "really" erased my data just in 30 seconds or something like that?

---

### Post by oldfred on 2009-11-27
Normal formats actually do not erase any data but make the drive available for overwriting the current data with new data. Actually unplugging the drive in the middle of that may have caused more problems than the actual reformat. As long as you do not write to a disk that is formatted often testdisk can recover most of the data. Of course you have backups.;)

Testdisk is available in the repositories and is often installed on recovery type liveCD's.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by shaggy999 on 2009-11-27
Depending on how important your data is you might actually want to look into buying a program. I'm all for open source but sometimes results matter more than free as in speech. To that end, and this isn't even a Linux application, but I used a program about 5 or 6 years ago called "GetDataBack for NTFS". They have a demo version of it, I believe, that will scan your drive and show you results but won't actually do the recovery part. I believe I paid about $100 for this program at the time. I used it to recover a 500GB RAID5 array and I was thoroughly impressed. I recovered something on the order of 98% of my files with filenames and everything intact.

I speak about this program merely from experience and it really saved my butt.

---

### Post by PRC09 on 2009-11-27
Also this one.

[http://www.diskinternals.com/](http://www.diskinternals.com/)

---

### Post by Yunus Emre on 2009-11-28
**oldfred** TestDisk didn't work for it. I've tried it as my first shot. Thanks anyway.

**shaggy999,** I'll try "GetDataBack for NTFS".

**PRC09,** did you use it somehow? Does it really work?

I've tried Disk Rescue II (for Mac) and R-Studio's disk rescue program. Both of them recovered most of my files but ordered them by checking file types, not folder structure. Since most of them are PSD's, CAD files and photos, this has no use at all.

---

### Post by zaphod777 on 2009-11-28
One vote for Get Data Back for NTFS I have recovered formated drives with this before.

---

### Post by Yunus Emre on 2009-11-28
I've started a disk scan with Get Data Back for FAT, since my disk was formatted with FAT. It says it will take like 6 hours. I'll make you know when it finished.

---

### Post by SR_ELPIRATA on 2009-11-28
I use File Scavenger for Windows and I've been able to recover data from both formatted and corrupted drives. Usually is a long process btw, so if u have a lot of data... get ready to spend some time while it scans and recovers files.

ELP

---

### Post by shaggy999 on 2009-11-28
The nice thing about GetDataBack for FAT/NTFS is that your 6-hour scan only needs to be done once. You can save the "results" to a "state file" and re-load them later when you're prepared to do actually recovery.

---

### Post by Yunus Emre on 2009-11-29
"GetDataBack for FAT" was the most succesful one among the ones that I've tried. Though it couldn't recover folder's names, it recovered all the files' and sub-folders' name. And it's much better than the others did. Thanks!

---

