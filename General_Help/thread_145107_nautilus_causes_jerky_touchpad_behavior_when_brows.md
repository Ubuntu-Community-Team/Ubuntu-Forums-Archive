---
title: "nautilus causes jerky touchpad behavior when browsing external hdds"
date: 2006-03-15
forum: General Help
---

### Post by droazen on 2006-03-15
Here's my problem:
I find that when nautilus is viewing folders with lots of items in them ( > 1000 or so ) on my external USB hdds, my touchpad pointer jumps erratically all around the screen, making it almost impossible to click on things. This persists until I close the folder in question. At first I thought this might be a software issue with nautilus - then I discovered that if I copy the directories in question to my internal IDE drive, nautilus can view them with no problems.

My internal drive has DMA enabled, which probably explains why nautilus has no probs handling large directories on it. But hdparm will not let me turn DMA on for my external drives (since they're not IDE) - and a few hours of searching through the forums suggests that it is not possible to enable DMA on a USB drive, at least not with hdparm.

So my question is: is there some setting I can enable on my USB hdds (perhaps using a util like sdparm) that will decrease CPU usage while accessing them, and hopefully get rid of the jerky pointer motion with nautilus described above? Or, alternatively, is there a way I can give my touchpad higher priority so that it won't be interrupted by hdd accesses? I've already set my touchpad as the CorePointer in /etc/X11/xorg.conf, but it doesn't seem to have helped.

I'd be grateful for any ideas...

---

### Post by droazen on 2006-03-16
After further investigation, I've discovered that this problem isn't the fault of either nautilus or the drive interface - the culprit is the gamin package, and in particular the gam_server process, which monitors the file system for changes. This is apparently a known issue with breezy's version of gamin, and is supposed to be fixed in Dapper.

---

