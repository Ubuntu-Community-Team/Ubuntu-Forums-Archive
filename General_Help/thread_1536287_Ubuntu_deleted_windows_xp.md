---
title: "Ubuntu deleted windows xp"
date: 2010-07-22
forum: General Help
---

### Post by soccertracker741 on 2010-07-22
I just tried to install ubuntu onto my computer from a disc. I got into the demo mode and started the install application. Everything was going ok but then a message popped up saying something failed to install. I tried once more to install and again it didn't work. Frustrated I restarted the computer to find that I couldn't boot from windows anymore. Instead I got a screen that said something along the lines of nothing to boot from. So now i'm stuck with a demo version of ubuntu and I'm pretty sure that my windows xp is gone.

Is windows actually gone?
If not how do I get it back?

---

### Post by anonymous1986 on 2010-07-22
Chances are that windows xp is still there. Your installation disc may have been faulty, always verify the disc at boot before installing.

First let's recover Windows XP, do you have a XP install cd?

---

### Post by soccertracker741 on 2010-07-22
unfortunately no

---

### Post by bhaverkamp on 2010-07-22
It would have been nice to have the full text of the error messages. If you boot into live mode with your CD and run 'sudo fdisk -l' to check if Windows is still there. You needed to be careful to make sure you chose the correct settings to repartition your drive during the install. This is no different than if you had tried to install another version of windows onto the same hard-drive.

---

### Post by soccertracker741 on 2010-07-22
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19076   153227938+  83  Linux
/dev/sda2           19077       19452     3020220    5  Extended
/dev/sda5           19077       19452     3020188+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


This is what came up when I did that.

---

### Post by soccertracker741 on 2010-07-22
If windows isn't there does that mean all of my files and the operating system are gone?

---

### Post by todak on 2010-07-22
> **soccertracker741 said:**
> If windows isn't there does that mean all of my files and the operating system are gone?
Unfortunately, yes. Apparently you inadvertently had the installer use your entire disk for Ubuntu, rather than accepting the default of dividing the disk space so that Ubuntu and Windows could both be on the drive.

---

### Post by soccertracker741 on 2010-07-22
ugh. that sucks. and of course there is no way to recover any of it?

---

### Post by Sef on 2010-07-22
> ...of course there is no way to recover any of it?

You may be able to recover XP.  

First, do not use the hard drive - use the live cd instead.  (The more you use the hard drive, the less you are likely to recover.)

Second, download [test disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can recover lost partitions.

or

Download it from Ubuntu's repostories.

---

