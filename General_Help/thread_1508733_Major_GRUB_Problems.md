---
title: "Major GRUB Problems"
date: 2010-06-13
forum: General Help
---

### Post by rchristy1 on 2010-06-13
Just installed dual boot with windows xp on master and Karmic on slave. Half of the time when I boot I get a grub rescue (cannot find disk error). Then sometimes after 6-7 minutes of GRUB loading I can finally get to the grub menu and boot. I have reinsalled and no change.

---

### Post by oldfred on 2010-06-13
The version of grub2 with Karmic would often go off and do a search if grub was on one drive and Ubuntu install was on the other drive. With older IDE drives you may have to switch master & slave settings which I am not sure will affect windows. Grub will have to be updated to add mapdevice command to let windows think it is still the first drive.

Reinstall grub to the Ubuntu drive and then switch master & slave settings. Then run
sudo update-grub

you could try editing out the search line in grub since you know it boots and see if that works as an alternative.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by rchristy1 on 2010-07-08
After several boots with the GRUB rescue coming up over and over again I installed Ubuntu 9.10 on the master (Dual boot w/ XP). I switched the settings on master and slave and set the BIOS to boot from master (since BIOS is no longer recognizing my slave drive). 

The computer will still freeze at least once a day requiring me to push the power button to restart. Upon restart I can hear the disk make a noise and I get a GRUB Rescue. After 5-6 tries I will finally get GRUB to start loading. After GRUB loads for 6-8 minutes I can finally boot up. I can see GRUB installed 2X (once on master and once on slave) should I get rid of it on the slave? If so how do I do so? 

Thank you in advance
Extremely Frustrated

---

### Post by oldfred on 2010-07-08
Having grub on the slave will not matter. 

I am concerned about your problems and they sound more like a hard drive failing than anything else. Hard drives are not supposed to make loud noises.

---

### Post by rchristy1 on 2010-07-10
Fred,

Looks like you were right. I pulled the slave out and tried to noot from master and got GRUB Rescue every time and that strange noise. Seems like GRUB on the slave was the only thing allowing the computer to ever boot. I wound up swapping the master out and have been running smoothly since then. That hard drive seemed to run fine until I installed Ubuntu on it, probably just a coincidence. Thanks for the help, I really appreciate it.

---

