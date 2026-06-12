---
title: "Ubuntu 10.04 Installation failed [errno 5]"
date: 2010-07-27
forum: General Help
---

### Post by Unknown-Demon on 2010-07-27
Hey everyone,
A few week's back I ordered a Ubuntu 10.04 LiveCD and I recived it just yesterday.
So I put it in the CD-ROM drive and rebooted my PC. First off when I went to install it, It gave me and error saying Installation failed because of an unrecoverible error. then I booted into the option "Try Ubuntu"
and started searching for a solution for the error online. I found a forum that was talking about the unrecoverible error and it said "Boot into Try Ubuntu and click the installation icon at the desktop"
So I did. Then I gave my information and such and then it started installing. then when it hit 41%
at copying files It gave me the error message saying that it failed and the error code was [errno 5]
I tryed following other steps online and they were all a no-go.
_
Replaced CD-ROM drive with spare - failed
Moved Desktop to another envirement - failed
Disabled Floppy drive - failed
Move memory chip to another bank - failed
Mark first 3 options in boot menu - failed
_

I am only able to get online using the live CD because I was dumb enough to delete windows ):
Any help would be appreciated!

___PC INFO___
DELL DIMENSION 2500
256mbs RAM
80 Gigabytes of memory
___

---

### Post by 3rdalbum on 2010-07-27
"errno 5" is "input/output error". It means that there was a problem reading from or writing to a disk. It usually means that a disk or drive is damaged or faulty.

As you have described ordering a pressed CD, then the problem is more likely to be in your hard disk, especially as the computer you describe is getting on a bit in age, and you've replaced your CD-ROM drive.

From the live environment that you are booted into, go to System > Administration > Disk Utility, click on your hard disk in the left pane and click "SMART data" in the right pane. "Reallocated Sector Count" and "Uncorrectable Sector Count" will show you if your disk is failing, if these values are getting close to their thresholds.

You cannot repair a disk in this state, only replace it.

Sorry to be the bringer of bad news!

---

### Post by Unknown-Demon on 2010-07-28
I see. Everything looked fine (in my case) just to be sure I put in another hard disk and took out the other to be sure. And
I still get the same error ;/
And I made a mistake on my pc info its:
___PC INFO___
DELL DIMENSION 2300
256mbs RAM
80 Gigabytes of memory
___

---

