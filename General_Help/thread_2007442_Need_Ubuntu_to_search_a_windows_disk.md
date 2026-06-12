---
title: "Need Ubuntu to search a windows disk"
date: 2012-06-20
forum: General Help
---

### Post by Tolipa on 2012-06-20
Hello, friends.  I have had a crash that was bad enough for me to buy another computer and start again.  The old CPU was IDE.  The root disk on the old computer (which has needed data),  would not load windows, but got into some kind of loop at the windows logo and stayed there.  After a couple of days of this I decided to use another older IDE machine (with windows 7), set the crashed data disk as the slave and reboot into Windows 7 and get my data.  Windows 7 would get into a loop and would not load (the crashed disk is in the slave position).

A friend suggested I make a Ubuntu boot disk, load that and look in the drive and remove what I wanted.  I loaded from the disk, but Ubuntu did not see the data disk or the Windows 7 root disk, even though the bios did. There did not seem to be a way to use Ubuntu to scan the attached disks.

So, I put the crashed data drive in the root position, and decided to load Ubuntu onto the drive as an operating system, and Ubuntu got into a loop and wouldn't load or install itself. Very tricky:)

The question is, is there a way to load Ubuntu from the Disk, and see other drives attached to the machine, and manipulate the files?

TIA
Frank

---

### Post by spiky001 on 2012-06-20
Hi

A good place to start would be to boot off of the cd, when the 1st screen comes up select try ubuntu without installing. (live cd).
Then open a terminal (top left dash home type in terminal), when terminal opens type```
 sudo fdisk -l 
``` that will list all drives post the output back here.

---

### Post by Mark Phelps on 2012-06-21
You need to know that if Windows filesystems get corrupted, especially if they are NTFS partitions, Linux may not be able to mount them.  

IF that happens, your primary recourse to recover data from those filesystems is to attached them to an MS Windows PC as external drives, and try running CHKDSK on them.

If CHKDSK doesn't work, you will then need to look into using MS Windows file recovery apps to try to get your data back.

---

