---
title: "*yawn* Installing Windows 7 alongside Jaunty"
date: 2009-07-22
forum: General Help
---

### Post by joey-elijah on 2009-07-22
What's the best way to approach installing Windows 7 alongside an existing Jaunty installation? 

I don't mind needing to reinstall GRUB etc (my grub is fluffed anyway! I need to hit F12 and choose a HD to boot from to fire up Ubuntu :p) 

I had a spare 40GB unused partition sat there, so i formatted it to FAT32 and I'm just wondering is that enough? Vista used to harp on about needing to be on a "boot disk" during installation which frustrated the hell out of me. 

Any ideas on what the best plan of attack is? If worst comes to worst, i will just nuke Jaunty, install Windows then WUBI Ubuntu back. Though I'd prefer to keep my existing very sweet set up :) 

Fankooo! :)

---

### Post by iFuzo on 2009-07-22
Use the partion you talked about which is not in use???

EDIT: Windows 7 installation is only 14GB if I recall

---

### Post by joey-elijah on 2009-07-22
> **iFuzo said:**
> Use the partition you talked about which is not in use???

EDIT: Windows 7 installation is only 14GB if I recall

That was my intention :D however i was wondering/asking whether Windows would install okay on to it given the other half of the drive has a Ubuntu partition and 'boot' sector malarkey? Should i format the partiton to FAT32 prior to installation or just leave it as unformatted?

---

### Post by dk06 on 2009-07-22
Wubi=safest

dual boot=my personal preference 
_______________________________

It's usually best to install windows 1st, then Linux 2nd 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Teabicky on 2009-07-22
Hi.  I have successfully installed windows 7 RC alongside jaunty.

I used a gparted boot disk to make space on my hard drive, check here for the live disk/ usb.

> [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I then installed windows as instructed... taking care to select the allocated space.  This all worked fine except that my grub was all messed up/gone and I couldn't access ubuntu.  For this I used supergrub, which is also I live cd, and that solved all my problems, it now all works like a dream.

Here is the link for supergrub....

> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by The-ITu on 2009-07-22
> **dk06 said:**
> Wubi=safest
dual boot=my personal preference 

It's usually best to install windows 1st, then Linux 2nd 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
out of curriosaty, (pardon this offtopic post)
may I ask, how exactly does wubi vary from dual booting in safeness?

---

### Post by dk06 on 2009-07-22
> **The-ITu said:**
> out of curriosaty, (pardon this offtopic post)
may I ask, how exactly does wubi vary from dual booting in safeness?


Installing an application in windows is less likely to hose your windows installation 
&
installing an operating system along side windows has higher potential error
(shrinking drive, installation errors, etc)

From personal experience, I've killed more Windows installations with dual-booting than I have with Wubi

---

### Post by joey-elijah on 2009-07-22
> **Teabicky said:**
> Hi.  I have successfully installed windows 7 RC alongside jaunty.

I used a gparted boot disk to make space on my hard drive, check here for the live disk/ usb.



I then installed windows as instructed... taking care to select the allocated space.  This all worked fine except that my grub was all messed up/gone and I couldn't access ubuntu.  For this I used supergrub, which is also I live cd, and that solved all my problems, it now all works like a dream.

Here is the link for supergrub....

Did you leave your 'allocated space' unformatted prior ot installation of Windows or already formatted?

---

### Post by Teabicky on 2009-07-22
> **joey-elijah said:**
> Did you leave your 'allocated space' unformatted prior ot installation of Windows or already formatted?

I did (i think), but you could use gparted to make the partition ntfs just for peace of mind.

---

### Post by Teabicky on 2009-07-22
Have you got all important information backed up?  It could still go "tits up".

---

### Post by joey-elijah on 2009-07-22
> **Teabicky said:**
> Have you got all important information backed up?  It could still go "tits up".

Doing that at this very moment! :)

I've unformatted the partition i want to install windows on, so hopefully it will work okay. Having to reinstall Ubuntu wouldn't be a major headache, but i'd prefer to keep my current set up because it's all nicely tweaked, updated etc.

---

