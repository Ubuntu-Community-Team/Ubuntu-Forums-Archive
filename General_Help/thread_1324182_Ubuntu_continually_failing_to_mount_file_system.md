---
title: "Ubuntu continually failing to mount file system"
date: 2009-11-12
forum: General Help
---

### Post by oddsocks1013 on 2009-11-12
Hey,

I'm running an Acer Aspire 5610z laptop, and today when I was trying to save a paper, it claimed it couldn't because the file system is read-only. I rebooted and was asked to run fsck manually. I ran fsck, fixed all of the errors and whatnot, and after another reboot everything started working fine.

This happened once on 8.10 Intrepid last month, and twice since I upgraded to 9.10 Karmic at the beginning of November. I did a fresh, clean install of Karmic and have had absolutely no other problems with it. 

Is this a known bug, or is this just yet another problem with this stupid laptop?

System Specs: 
Operating System: Ubuntu 9.10 (Karmic), Linux Kernal 2.6.31-14-generic, GNOME version 2.28.1
 Memory: 2063 MB
Processor: 2x Genuine Intel CPU   T2060 @ 1.60GHz
 Hard Drive: ATA Hitachi HTS54168 [80GB total, 42GB Ubuntu partition]

The laptop's about 3 1/2 years old now, if that has any bearing on the situation.

Again, apart from the failure to mount the file system on startup, I'm having no other problems with Karmic (I'm given to understand that I'm sort of in a minority there).

I would kind of like to know why this is happening, and how to fix it permanently. Running fsck every now and then on startup is fine, but I'd kind of like whatever's going on to stop altogether.

---

### Post by falconindy on 2009-11-12
If a drive is remounting itself as read-only, it's because it's encountering write errors and remounting itself in an effort to protect the data. If fsck clears these errors but they continue to occur, it may be a sign of a failing hard drive.

**At your own risk:** If you want to ignore these errors or you think they're false positives, you can edit your /etc/fstab to remove the "errors=remount-ro" option on the drive.

---

### Post by oddsocks1013 on 2009-11-15
Hey,

Just to update on the issue, it seems to have suddenly started happening much more often. It happened Friday afternoon, and again this morning (whereas before there was at least a week between incidences).

I'm trying to see if the Windows partition has errors, but so far Disk Check has been less than helpful, though CCleaner is turning up a lot of registry errors that probably shouldn't be occurring (since I rarely use that partition for anything other than movies or games).

If this helps me, let me know.

---

