---
title: "Wubi and Ubuntu 11.10"
date: 2012-03-24
forum: General Help
---

### Post by thermanshs on 2012-03-24
Hello all, I'm a fairly new Ubuntu user and since I'm mostly on windows I chose the Wubi method.
So: I have 2 disks, 1 60GB for windows and the other is 1TB partitioned in 2 units, first 60GB is for Ubuntu 11.10 and the rest is for media storage.
So I set Wubi pick my 60GB partition on my 2nd disk and everything went fine Ubuntu up and running. Problem is I tried to install some stuff and my disk space is reporting as insufficient!!! On Windows I see that Ubuntu's partition is only using 14/60 GB. When I load Ubuntu and enter Computer I can see the 1TB hard disk , the 60GB hard disk and then the Filesystem. Opening the 1TB hard disk which is the physical container of Ubuntu opens me the media storage partition, which is ok. When I open the Filesystem I hop into root directory. But right clicking the Filesystem partition to see the space available it says that contents take up 140*TB* of space and then there's only a few MB free.
Anyone know how to help?
Thanks in advance,
George

---

### Post by wildmanne39 on 2012-03-24
Hi, if you used wubi it only creates like a 17 gig partition inside your window partition, you can use a usb hard drive to store your files on our you can reinstall or migrate the wubi install to a true dual boot, here is a link for migrating.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
Thanks

---

### Post by cfhowlett on 2012-03-26
Wubi is NOT a long-term installation solution - it's for TRYING ubuntu.  (So says the developer). 

I'm guessing you have a healthy amount of ram.  I suggest you install virtualbox in windows, install ubuntu inside virtualbox and go about your day.  Once you decide to do things the right way, install ubuntu in dual boot configuration.

---

