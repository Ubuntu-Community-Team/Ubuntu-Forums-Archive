---
title: "GRUB and MBR: help needed with mounting clones"
date: 2010-04-05
forum: General Help
---

### Post by itendo on 2010-04-05
I have been struggling with my computer crashing randomly in bothy vista and karmic for about three weeks now and only after two serious days of fighting have I been able to put together a real diagnosis and post. any help is greatly appreciated (pc specs listed in sig):

My computer was screaming about problems with reallocated sector errors in ubuntu (thanks windows for not saying or doing a thing until it was waaay too late). I cloned 1 vista and 1 karmic partition off the failing hard drive to my second hard drive. (it performed a file for file clone, rather than an image). [note: for the Vista partition I had to run chkdsk /r to get it in shape for cloning and it would fail around 150k/180k indices on stage 2, but through some luck booting into vista it started a chkdsk /r off the bat and repaired it before it subsequently crashed.]

I tried wiping and zero erasing the bad hard drive, and have followed up with RMA’ing Seagate because it appears that there is a platter going bad or something. Anyway, so at this point I have one 1T Seagate (dead), one 1T Seagate (healthy), and 1 320gig WD. 

I was hoping that I could at least redo the MBR & boot record in order to get the computer to boot into GRUB and give me access to my two OS partitions. This failed. I am not sure how to manually manage this as trying to setup GRUB from a liveCD didn’t get me anywhere even after regenerating the device.map and grub.conf because I still couldn’t root any hard drives. [There was 1 267gig Vista partition, 1 88gig 9.04 Ubuntu partition, and 1 370gig media/apps partition. The files from the media/apps partition (about 80 gig) are also backed up on my second hard drive (the 320 gig WD).]

Basically it seems the current issue is getting a boot sequence in place that mounts the OSs in my system. To try to automagickally flush my MBR and boot sector I installed the beta 1 of 10.04 Ubuntu to a partition on the 320gig WD (the second hard drive). During setup it recognized both of the other OS's and imported their settings. On finish and reboot, however, I got a non-responsive black screen without even a boot error. Then, I used the program Smart Boot Manager to find out if I could at least boot the new Ubuntu partition on its own after hiding the other two; subsequently I tried every variation on boot sequence and availability I could. All met with failed boots. 

I saw one thread here talking about people installing Lucid Beta 1 and getting a black screen on reboot and no log in screen and that may be the problem (probably should have added a stable distro), but I have a feeling it is not.

---

### Post by oldfred on 2010-04-05
Depending on how you copied, you either have duplicate UUIDs with the old drive and if old drive is still on the system may be confused or you have new UUIDs and grub & fstab all have to be updated.

If a reinstall of grub and verifing UUIDs in fstab do not solve problem post this script to see entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by itendo on 2010-04-05
thanks i will follow up. i am planning to take another shot at correcting grub, starting with finding a menu.lst.

---

### Post by oldfred on 2010-04-05
If you have a new install of Karmic you have grub2 and no menu.lst.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

