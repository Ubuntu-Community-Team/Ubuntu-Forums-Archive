---
title: "ubuntu freezes at login screen"
date: 2006-03-17
forum: General Help
---

### Post by pk_volt on 2006-03-17
I installed ubuntu 64 bit version on my compaq presaro v2570ca laptop.

I used resier FS and a primay swap partition of 300 megs.

uumm.   Everytime I get to the login screen, everything works fine, until you wait for maybe 5-6 seconds, it'lll freeze up and I an't do anything.

I installed version 5.04

thanks

---

### Post by pk_volt on 2006-03-18
top?

---

### Post by lopzided on 2006-03-31
i am having the same problem. when i get to the login screen, everything freezes...i cannot use the mouse or the keyboard. occasionally, i have a few seconds where i can type my user name and password, but as soon as gnome gets past the splash screen, i get the desktop and it freezes again. the only thing that gets loaded is the taskbar and the top menu bar (minus the system tray and the clock).

i have tried formatting/repartitioning/reinstalling, but the same problem occurs. right now i am reinstalling using ext2 instead of ext3, as was suggested in the #ubuntu channel on freenode. if that doesn't work, i will check my system clock (although i'm almost positive it's right), and post back my results.

also, as a side note, my installation worked perfectly fine, until i moved yesterday...when i set my computer back up, that is when the problem began. i am still able to boot up from a livecd (i used knoppix), and even mount the drive, but it appears that the drive is being mounted as read only.

**EDIT** : reinstalling using ext2 did not solve this problem

---

### Post by lopzided on 2006-03-31
ok, i checked my system clock, and it was off by roughly 7 hours...after adjusting, i rebooted, and a bunch of errors about inodes and things being fixed came up...then i was dropped into a root shell and told me this:

/: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY

i did so, and this was the outcome: 

*NOTE: don't know if this matters or not, but this is after reinstalling using ext2

/ contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 954186
Connect to /lost+found<y>?

i didn't know what to do here, so i followed the default, yes...which produced:

Inode 954186 ref count is 2, should be 1.  Fix<y>?

Well, fixing sounds good...once again, i went with the default yes.

Inode 4014081 ref count is 10, should be 6.  Fix<y>?

went with yes again...then got this crazy message:

Pass 5: Checking group summary information
Block bitmap differences: -1573382 -(1574912--1574917)  .... and this went on for about four lines

Fix<y>?

went with yes again..

i went with yes for all of the following as well:

Free blocks count wrong for group #48 (32190, counted=32250)
Fix<y>?
Free blocks count wrong for group #57 (30702, counted=30710)
Fix<y>?
Free blocks count wrong for group #58 (25074, counted=25005)
Fix<y>?
Free blocks count wrong for group #245 (32224, counted=32246)
Fix<y>?
Free blocks count wrong (8984922, counted=8984943)
Fix<y>?
Inode bitmap differences:  -(786437--786477) -954185 +954186 -(4014083--4014109)
Fix<y>?
Free inodes count wrong for group #48 (16339, counted=16380)
Fix<y>?
Directories count wrong for group #48 (26, counted=2)
Fix<y>?
Free inodes count wrong for group #245 (16345, counted=16372)
Fix<y>?
Directories count wrong for group #245 (10, counted=5)
Fix<y>?
Free inodes count wrong (4694205, counted=4694273)
Fix<y>?

which produced

/: ***** FILE SYSTEM WAS MODIFIED *****
/: ***** REBOOT LINUX *****
/: 73471/4767744 files (0.2% non-contiguous), 535569/9520512 blocks

and sent back to root...

so i rebooted with reboot command at prompt...and the same problem happened!  

help!

---

### Post by lopzided on 2006-03-31
okay, i managed to move quick enough to choose gnome failsafe from the session menu, and it booted...it didn't freeze!  this is after rebooting several times, each time getting error messsages about fsck and being forced to reboot in mid-boot....now that i am in gnome-failsafe, the mouse moves, but very slowly and choppy (on my p4 2gig)...however, clicking the menu at the top doesn't do anything, nothing pops down for me to choose...so i'm pretty sure i can't do anything with gnome-failsafe.

what do i do?  i want my ubuntu back!  :(

---

