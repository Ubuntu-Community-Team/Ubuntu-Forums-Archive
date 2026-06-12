---
title: "Login screen not showing on startup"
date: 2010-05-12
forum: General Help
---

### Post by Saser on 2010-05-12
I just installed Ubuntu 10.04 Lucid Lynx 32-bit version from CD. I can successfully start Ubuntu after the installation is complete, but when I reboot my computer and choose Ubuntu in GRUB, I only come to a screen where the mouse cursor and default background image is shown. No login screen. I can move the mouse around, and if I press the power button of my computer the menu shows up where I can choose to either Shutdown, Restart, Suspend or Hibernate. The Help button on that menu doesn't seem to work; nothing happens when I press it. Also, when I boot from the CD, it says that "The installer encountered an unrecovable error. A desktop session will be started instead" or something like that, I don't remember the exact words.

Sorry for flaws in my English; I'm just a 15 year old guy from Sweden.

---

### Post by DeMus on 2010-05-12
> **Saser said:**
> I just installed Ubuntu 10.04 Lucid Lynx 32-bit version from CD. I can successfully start Ubuntu after the installation is complete, but when I reboot my computer and choose Ubuntu in GRUB, I only come to a screen where the mouse cursor and default background image is shown. No login screen. I can move the mouse around, and if I press the power button of my computer the menu shows up where I can choose to either Shutdown, Restart, Suspend or Hibernate. The Help button on that menu doesn't seem to work; nothing happens when I press it. Also, when I boot from the CD, it says that "The installer encountered an unrecovable error. A desktop session will be started instead" or something like that, I don't remember the exact words.

Sorry for flaws in my English; I'm just a 15 year old guy from Sweden.

Hi,
It looks to me you have either a bad cd or something just went wrong with the installation.
The error you describe tells you that you are working on the live CD. When you want to install Ubuntu you can either try it again, or better download another copy, burn it again (use low speed) and try the installation again.
Don't apologize for your English, it is perfect.

---

### Post by Saser on 2010-05-12
Thanks, I'll try that tomorrow, it's late here and I'm too tired to do it right now. :P

I had the same issue when I installed the 64-bit version. But after a while I found out that the iso image I downloaded had the ending ..._amd64.iso. Since I use a Intel Core 2 Duo E8400 @ 3.0GHz processor I thought that maybe my processor could be the problem. But it seems that there's something else that is the cause.

---

### Post by DeMus on 2010-05-12
> **Saser said:**
> Thanks, I'll try that tomorrow, it's late here and I'm too tired to do it right now. :P

I had the same issue when I installed the 64-bit version. But after a while I found out that the iso image I downloaded had the ending ..._amd64.iso. Since I use a Intel Core 2 Duo E8400 @ 3.0GHz processor I thought that maybe my processor could be the problem. But it seems that there's something else that is the cause.

I'm not sure your processor can handle 64-bit software. I think so because otherwise the error would be different: wrong architecture or something.
Just download again, burn it again and go for it. Success.

---

### Post by Saser on 2010-05-12
My processor can in fact handle 64-bit software; I'm using Windows 7 Home Premium 64-bit on the same computer. :P
You can read about my processor [here]("http://www.intel.com/products/processor/core2duo/specifications.htm").
What I meant was that maybe the fact that my processor was an Intel with 64-bit maybe didn't work well together with Ubuntu 64-bit; amd64 seemed to me that it was only for AMD processors with 64-bit support.

---

### Post by Saser on 2010-05-12
What is a good writing speed? 1x? That seems like it's gonna take forever.

---

### Post by DeMus on 2010-05-13
> **Saser said:**
> My processor can in fact handle 64-bit software; I'm using Windows 7 Home Premium 64-bit on the same computer. :P
You can read about my processor [here]("http://www.intel.com/products/processor/core2duo/specifications.htm").
What I meant was that maybe the fact that my processor was an Intel with 64-bit maybe didn't work well together with Ubuntu 64-bit; amd64 seemed to me that it was only for AMD processors with 64-bit support.

They call it Ubuntu AMD-64 but it also works on Intel processors. A name-change would be good here.
I had 64 bit software for 2 years (Hardy and Jaunty) but now I use the 32-bit version of Lucid because of Flash problems in the 64-bit version.

To answer your last question: 1x is very slow, but don't use the maximum to burn the CD. A speed of 8x or maybe 16 times is good.
Success.

---

### Post by uRock on 2010-05-13
I agree, running a slower burn should help. I run 4x when burning to DVD and 16x when burning to CD.

---

### Post by theviking10 on 2010-05-13
Bumping for relevance. Fresh install, no login screen. Burning a new disc.

---

### Post by uRock on 2010-05-13
Let us know how the new burn goes.

---

### Post by Saser on 2010-05-14
Now my Ubuntu works perfectly. It seems that I get this problem when I compile and install a few packages from their sources, like libpng and zlib.

---

### Post by craigymitchell on 2010-05-14
Hi have seen a similar issue with Ubuntu 10.04 Lucid Lynx on a Samsung P210. I upgraded from Karmic and have had no major issues except when booting up running on battery power when I get to the login screen there is no login box just the shut down menu in the bottom right corner. Even stranger is that this fault is intermittent so if I shut down and reboot everything will go as normal. When running on mains power the issue never surfaces.
Any thoughts or ideas to solve this would be great.

---

### Post by theviking10 on 2010-05-14
No dice for me - still no login screen. (using a Toshiba Satellite A505-S6005)

I noticed that the install sort of hangs when ext4 is introduced to the hard drive. Maybe this is the culprit?

Also, I can only boot any linux live using AHCI SATA command. Live, Ubuntu works perfectly. The install is also flawless, or so it appears. The problem only arises when I try to log in.

---

### Post by uRock on 2010-05-14
> **theviking10 said:**
> No dice for me - still no login screen. (using a Toshiba Satellite A505-S6005)

I noticed that the install sort of hangs when ext4 is introduced to the hard drive. Maybe this is the culprit?

Also, I can only boot any linux live using AHCI SATA command. Live, Ubuntu works perfectly. The install is also flawless, or so it appears. The problem only arises when I try to log in.
You should start your own thread, so that it gets the proper attention. The OP's problem has been solved.

If EXT4 were the culprit, then none of my machines would be running.

---

### Post by LittleGyko on 2010-07-14
> **Saser said:**
> Now my Ubuntu works perfectly. It seems that I get  this problem when I compile and install a few packages from their  sources, like libpng and zlib.

i installed zlib today and got this problem. does anyone know of any solution other than a complete reinstall of ubuntu.

thanks

---

### Post by Raikiri on 2011-08-24
> **LittleGyko said:**
> i installed zlib today and got this problem. does anyone know of any solution other than a complete reinstall of ubuntu.

thanks

Old topic but I have this exact same problem, three people in this thread have now mentioned it.  Bloody zlib.

Any solutions anyone? Apart form a fresh install?

---

