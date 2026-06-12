---
title: "Xubuntu 10.4 on Toughbook CF-29"
date: 2010-05-27
forum: General Help
---

### Post by Arch_NME on 2010-05-27
I'm trying to install Xubuntu 10.4 on a Panasonic Toughbook CF-29 (Pentium M 1.4, 768MB ram).  I downloaded the i386 desktop iso and burned it to a disk to install.  When I go to install it freezes though. I tried it a couple times and one time when it froze I hit ALT-F1 and I saw this error message about squashfs repeating over and over. I thought maybe it was a bad disk at first so I burned another one and tried, same issue though. Then I thought maybe the ISO was bad so I downloaded another one from a different server. Burned another disk same issue. Ran md5sum util on the ISO it is is definately good. Was able to try one of the disks in another computer and it was able to work as a live cd (which it would not on the toughbook).  This toughbook is known to be good because I have a Ubuntu 9.10 live CD that runs on it and I tried installing XP on it and that worked.  I don't think there is any problem with the computer.

So... I'm stuck. It looks like I have a good disk and a good computer. Why won't the two cooperate with eachother? Any suggestions on how to get this to work or what could be going on?

---

### Post by Arch_NME on 2010-05-28
I got it to install using the alternate 386 iso.  Unfortunately now on boot after the xubuntu name appears for a few seconds it then goes blank and freezes.

---

### Post by dino99 on 2010-05-28
try to boot with nomodeset on the boot line

which graphic card is used ?

related links:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/577256](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/577256)
[http://kubuntuforums.net/forums/index.php?topic=3111694.0](http://kubuntuforums.net/forums/index.php?topic=3111694.0)


[http://biobug.org/toughbook/](http://biobug.org/toughbook/)
[http://ubuntuforums.org/showpost.php?p=7348742&postcount=5](http://ubuntuforums.org/showpost.php?p=7348742&postcount=5)

---

### Post by Procuro on 2010-06-09
Hi, I had the same problem and discovered that all the intel i855 graphics chipsets have the same problem in 10.04. Thankfully it's an easy fix, you just have to add "i915.modeset=1" to your kernel boot options and it'll load. Check this link for more info: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Now I'm trying to figure out how to calibrate the touchscreen properly :confused: Let me know if you have any luck with that.

---

### Post by tbuser on 2010-07-03
> **Procuro said:**
> Hi, I had the same problem and discovered that all the intel i855 graphics chipsets have the same problem in 10.04. Thankfully it's an easy fix, you just have to add "i915.modeset=1" to your kernel boot options and it'll load. Check this link for more info: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Now I'm trying to figure out how to calibrate the touchscreen properly :confused: Let me know if you have any luck with that.
I want to thank you for the information re: i915.modeset=1. Without it I would not have gotten past the splash screen and then solved several issues. Here is the answer to your question about touchscreens. 
[http://forum.notebookreview.com/panasonic/496467-cf-29-ubuntu-10-4-success.html](http://forum.notebookreview.com/panasonic/496467-cf-29-ubuntu-10-4-success.html)
As I used a convoluted method of obtaining the right numbers and as they work very well I am not going to risk calibrating yet. You could try the numbers shown and then change them in small increments. That is the least important. I recommend following the script exactly. You need hal and you need /xserver/xorg/input/evtouch.
As I stated follow the plan and good luck to you.
I always tune up the Touchpad as shown too.

---

