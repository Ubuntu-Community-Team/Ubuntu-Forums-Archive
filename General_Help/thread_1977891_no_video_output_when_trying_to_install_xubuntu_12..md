---
title: "no video output when trying to install xubuntu 12.04"
date: 2012-05-10
forum: General Help
---

### Post by supernater on 2012-05-10
I was trying to install xubuntu 12.04 on my computer and I don't see a splash screen or anything when the CD is running.  The screen goes blank and I see a command prompt.  The CD seems to load just fine because I can hear the DVD drive working.  When I use the same installation CD in my laptop, it works fine, I can see the xubuntu splash and the option to try or install xubuntu is presented.  Is the video driver that the installation cd uses the problem?  My computer has a GTX 550 Ti.  Is there any way to install this?

---

### Post by danix803 on 2012-05-10
This might help... It's from [TheDanishProject]("http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/") ... 
 
Try these steps if you are experiencing a blank screen during boot or install of Ubuntu 11.04 Natty Narwhal.
 
1. LiveCD  boots into a blank screen.
 
When you see the boot menu when you boot LiveCD, hit F6 and select the “nomodeset” option.
 
2. Boots into a blank screen after install.
 
Reboot and keep your finger on the “SHIFT” key till you get the grub menu. Highlight the first entry and replace “quiet splash” with “nomodeset” .  Hit CTRL + X to continue booting. 
 
Once logged in install the latest Graphics drivers. *System -> Administration -> Additional Drivers*

---

### Post by supernater on 2012-05-11
Option 1 worked!  I reinstalled and during the installation the proper Nvidia drivers were loaded, I think it was nvidia-current 295....?  Anyway, everything worked fine upon reboot.  Thanks!

Just to be clear on what I did, what does nomodeset do?

---

