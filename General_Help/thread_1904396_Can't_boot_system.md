---
title: "Can't boot system"
date: 2012-01-04
forum: General Help
---

### Post by zaqwes on 2012-01-04
I've had ubuntu 11.10 with 3.0.0.14 kernel working but sound was off, so I was using 3.0.0.13 which started having some problems. So, I decided to upgrade kernel to 3.1. Upgrade went perfectly (no error messages) but after reboot there is violet screen.

I turn computer on and I have GRUB properly working, I choose 3.1 version and I have the violet screen or there is logo with dots, they turn all red, logo dissapears and I get violet screen. ctrl+alt+f[sth] doesn't work, the same with power button. I tried choosing older kernel version, I get black screen with some things turning on, everything is ok, and it stops (no log in screen) I can press power button and it works, and turns computer off. 
I made livecd on pendrive but it gives "boot error". I wnet to recovery mode and tried startx(gives blackk screen with locked mouse), initx (white terminal window in the corner in which I can't write anything). I don't now what I wrote but it gave something about Xorg problems. I also got i915 symbol problem ( which I think I've seen before with working system I have intel i5 and I've read it always gives it when there is no other graphics card on). I found a lot of similar problems but most of them was either to update, or nVidia problems - I have radeon card hd 5650

I tried 
```
apt-get install --reinstall linux-image-generic
```
it went without problems but showed me that I have 3.0.0.15 kernel version

---

### Post by wildmanne39 on 2012-01-04
Hi, have a look at this link it may help, it is possible that since you upgraded your kernel you will need to use a boot parameter until you install your video card driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by zaqwes on 2012-01-05
Thank you for answer
I tried all the options and nomodeset in older versions of kernel  got me violet screen with Ubuntu and red dots, then there is a quick red statement, which I can't read. 
As quiet splash is not in the end of the line I tried this
[http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/](http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/)
but it didn't even give me logo.

---

### Post by wildmanne39 on 2012-01-05
Hi, I am not an expert with kernel issues, I will leave this to a someone more experienced with this issue.
Thanks

---

### Post by cariboo on 2012-01-05
Moved to General Help, as your problem occurs even before the Desktop environment is loaded.

---

### Post by zaqwes on 2012-01-06
I managed to get liveCD working (bios problems), so I updated the system using chroot and there where some update problems considering only flash. Then I tried uninstalling flgrx and after some problems I made it, but after intalling proper ATI drivers  still won't boot.

So now I am in there:
-got kernel 3.1, 3.0.0.15 which I did not install but looks like it's the "actual" one, 3.0.0.14 and those older
-none of the versions works properly, using 3.00.15 I get logo screen without any mistakes but 5 dots get red in one time and then I get black screen with statements what is turning on and I can get to console with ctrl+alt+f1
-ati driver install went without problems and aticonfig exists

I don't have any ideas what to do left, and I am pretty annoyed with all of this, but still don't want to do clean install, as I can always loose some configuration files

---

