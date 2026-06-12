---
title: "recover data from wiped hard drive"
date: 2009-09-22
forum: General Help
---

### Post by mr_sexy on 2009-09-22
hi, I'm pretty new to this open source stuff and I could really use some help.  I formatted my hard drive and installed ubuntu 9.04 because windows vista totally sucks and I forgot to back up some important files I had before I did that, is there any way that I can recover these files?  I've been looking all over for help and haven't been able to find much

---

### Post by GoldenSun on 2009-09-22
google a program called "photorec"

I used it a few times to grab some deleted files off flash drives.

---

### Post by HereInOz on 2009-09-22
You are probably at the stage of finding a professional data recovery organisation, who will perhaps be able to assist.

Data is fairly easy to recover from a formatted drive, provided you have not re-installed anything on it.  Once something else is installed, recovery of the data in the area where the new files are written can often be a heartbreaking experience.  If the data resided on an area of the disk which has not yet been written to, a data recovery mob may get lucky, but it won't be cheap.

You could try something like SpinRite from grc.com, but it will be a bit of a lottery as to what you can recover, and it may make the task of any professionals more difficult.

---

### Post by t0p on 2009-09-22
I have nothing reassuring to add to what's already been said.  You wrote that you formatted the drive then installed ubuntu onto it.  Well, the data may have survived the format, but installing ubuntu may have finished it off.

Any data that has been physically overwritten is lost.  Read [this]("http://mirror.href.com/thestarman/asm/mbr/WIPE.html#note") for more insight to the problem.  Professional data recovery services may be able to get some of it back.  But then again, maybe they won't.  And they'll charge you lots of money either way.

Maybe you should just write off what's lost, and put it down to experience.  At least now you know not to format a partition without backing up your data first.

---

### Post by bitterbug on 2009-11-01
I just got bitten by this issue too.

I was having trouble getting 9.10 to install from an SD-Card, so I dug out my 9.04 image and was trying to burn it to the card instead. I guess the reason 9.10 wouldn't work was because the card reader on my desktop machine was acting flaky when I thought it was the laptop.

Long story short, I selected the flash card (2GB) and chose to make it bootable. Drives unmounted and remounted, and when I looked my PVR drive with 1 Terabyte of archived shows was now a 900 meg Ubuntu installer drive. 

I almost wet my pants.

Still don't know how it pulled that off, since I was watching shows on it at the time. Shouldn't it have refused to wipe a drive that was being used?

---

