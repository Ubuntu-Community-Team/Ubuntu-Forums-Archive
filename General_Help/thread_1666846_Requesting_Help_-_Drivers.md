---
title: "Requesting Help - Drivers"
date: 2011-01-14
forum: General Help
---

### Post by jamie-khan on 2011-01-14
I've just built my first PC. The motherboard came with a driver disk, I tried installing this when I turned on the computer for the first time but the disk was not recognized. 

So I went ahead and installed Ubuntu from a burnt ISO disk with no problems (which was a relief for me because I thought if the driver disk was not working I may have some problems). Now I have Ubuntu running fine but no drivers or utilities for my motherboard, I cant play music or video so I assume I am missing allot of software.

I have tried entering the driver disk again but the computer doesnt pick it up, I've tried taking the computer apart and switching the IDE leads and selecting the drive on BIOS but everytime I hit ESCAPE to load bootable media it waits a few seconds, I hear the disk drive starting but it loads straight to Ubuntu.

The computer is not connected to the internet yet so I was wondering if you could tell me weather I can download the drivers I need through Ubuntu, or weather it is better to keep trying to install the drivers and utilities from the disk. If you think it is important to have the drivers from the disk then do you have any advice on how to install them (I know this part is not really an Ubuntu issue).

Any help is appreciated, I'm not at all sure what I'm doing.

---

### Post by anglican on 2011-01-14
> **jamie-khan said:**
> I've just built my first PC. The motherboard came with a driver disk, I tried installing this when I turned on the computer for the first time but the disk was not recognized. 

So I went ahead and installed Ubuntu from a burnt ISO disk with no problems (which was a relief for me because I thought if the driver disk was not working I may have some problems). Now I have Ubuntu running fine but no drivers or utilities for my motherboard, I cant play music or video so I assume I am missing allot of software.

I have tried entering the driver disk again but the computer doesnt pick it up, I've tried taking the computer apart and switching the IDE leads and selecting the drive on BIOS but everytime I hit ESCAPE to load bootable media it waits a few seconds, I hear the disk drive starting but it loads straight to Ubuntu.

The computer is not connected to the internet yet so I was wondering if you could tell me weather I can download the drivers I need through Ubuntu, or weather it is better to keep trying to install the drivers and utilities from the disk. If you think it is important to have the drivers from the disk then do you have any advice on how to install them (I know this part is not really an Ubuntu issue).

Any help is appreciated, I'm not at all sure what I'm doing.Your motherboard driver disk is almost certainly for Windows only, and not bootable. Had you installed Windows on your hard-drive it may have been useful for the drivers needed for your motherboard, but for Ubuntu is quite useless. Usually Ubuntu finds everything it needs when you run the install CD - are you certain that any of your hardware has not been correctly identified and configured? If anything isn't working with Ubuntu a reasonable place to start is:
```
sudo lspci
```to identify the hardware and ```
dmesg
``` to see what errors (if any) are occurring.

H

---

### Post by jamie-khan on 2011-01-14
Ah-ha Ok, I had no Idea that was the case, I assumed the drivers and utilities were for the motherboard to use for any OS... I need to read more.

Thanks for your help.

---

### Post by sanderj on 2011-01-14
Maybe proprietary drivers are needed. If so, you should see in the right upper corner a green symbol of a hardware part (some like a ethernet card or graphics card). 

Make sure you're connected to Internet when you click on that icon, as that tool will download drivers from Internet AFAIK.

---

