---
title: "Ubuntu on Toshiba AC100?"
date: 2011-07-13
forum: General Help
---

### Post by vickoxy on 2011-07-13
Hi,
just wanted to aks if anyone here has full-functionally Ubuntu running on AC100. So, maybe some how-to?
Is it possible to upgrade RAM to 1 or 2 GB?

---

### Post by peter d on 2011-07-13
Don't have an AC100 but it looks like it could run Ubuntu without too much trouble. You'd need to install it from a USB drive. Maximum RAM is apparently 1Gb.

---

### Post by vickoxy on 2011-07-13
Thanks for answering-unfortunately, all reviews i read reporting pretty much stuff are not working.
I would try to install only Ubuntu on SSD to make it quicker. But does it really support more than 512 MB RAM?
Another thing-is there openoffice/office suite for android 2.1 or 2.2?

---

### Post by ChaoZero on 2011-07-26
I do have an ac100(-10T) running ubuntu 10.10 on a 2.6.32 kernel.

Pretty much everything is working the way it should.
Working:
-video 2d+3d acceleration
-flash
-sound
-suspend
-wifi
-3G modem
-bluetooth
-hdmi

issues:
-no sound over internal speakers. headphone works
-flash tends to crash
-sometimes wifi doesn't work after suspend
-hdmi maximum resolution is 640x480 :-\
-upgrade to 11.04 works, but causes the system to be less stable. 

Even without understanding what you are doing you can get this up and running. Just stick to the tutorials...
[http://ac100.tunk.org/wiki/phh](http://ac100.tunk.org/wiki/phh) or [http://www.o-learn.com/content/howto-install-ubuntu-on-toshiba-ac100](http://www.o-learn.com/content/howto-install-ubuntu-on-toshiba-ac100)

Openoffice can be installed from the software center. Haven't noticed any problems using it so far.

Overall the support from nvidia isnt what it should be (or at least not like their gpu-drivers), and my ac100 is usable but not perfect. It's super-portable and now running ubuntu im pretty happy to have it.

It's still more of an enthousiast's gimmick than a consumer laptop - glad i'm an enthousiast :D

---

### Post by pibach on 2011-07-27
Thanks for the info. I too have an AC100. No Ubuntu on it yet, but I consider converting to it. Just some questions:
Did you install on the internal memory, SSD? Did it make a huge difference in performance?
how does the performance compare to the android install, let's say for browsing the web? Does the tegra 2 handle Ubuntu fast enough?
 And what about power consumption? I do get 6 to 7 hours runtime with android. Can I expect the same with Ubuntu?

---

### Post by vickoxy on 2011-07-27
Thanks for answers! The same question here-did you installed it on SSD? Please, if someone has HDMI full Resolution idea - post it here (i have monitor with 1920x1080)...

P.S. Under Android - can it have 1920x1080?

---

### Post by ChaoZero on 2011-07-27
I installed ubuntu on internal eMMC, which is fast enough.
Right now i'm back to using nilfs2-filesystem, for ext3 felt less snappy. I didn't try running from ext4-fs yet. Running from internal storage definetely boosts performance compared to running from SD-card or USB.

The tegra2 seems to handle ubuntu pretty well. Boot time is less than a minute and browsing the web is no problem at all. Only downside is the fact flash crashes from time to time. I'd say browsing is as fast as any 1st-gen dualcore atom packing 512 megs of ram.

As far as power consumtion is concerned, i think it's fair to say you'll get ABOUT THE SAME battery time. Ofcourse it depends on what you're doing, however i had no problem streaming 720p video from my nas for about 3 hours straight, and using it to browse the web for another 2 hours before i needed a recharge. backlight was at about 50%, and the ac100 was suspended for about 45 minutes in between playback. Note: ubuntu doesn't give u an indication on the battery time, but just keeps saying "estimating...". I got at least 5 hours of functionality plus 45 mins suspend, plus whatever was left when i felt like plugging in the power: it was not drained yet:)

About HDMI: I haven't tried this myself. My monitor is 1920x1080, but only has a DVI connector. However i read it's necessary to stop gnome (service gdm stop) and restart x11 on the external screen.
See this bugreport: [https://bugs.launchpad.net/ac100/+bug/806556](https://bugs.launchpad.net/ac100/+bug/806556)
I do not know about hdmi under android, because i didn't use it:) started off installing ubuntu right away. I do know 2.1 could only clone the internal screen (1024x600).

About upgrading ram: I wouldn't count on it. I haven't opened mine but I don't think there will be a convenient expension slot;)

---

### Post by vickoxy on 2011-07-27
Well, because it is fanless i tend to use it more often. You think it could be performance (openoffice/pdf reader) as some atom single core netbook (with 1 GB RAM)?

---

### Post by paultrafalgar on 2011-07-28
The battery estimating thing fooled me too! If you double-click it you get a pop-out panel with all sorts of useful detail.

---

### Post by pibach on 2011-09-27
> **ChaoZero said:**
> 
-upgrade to 11.04 works, but causes the system to be less stable. 

I have an AC100 running Lubuntu Oneiric (with more lightweigth LXDE instead of Unity) and can confirm that with todays kernel update bringing Headphone sound, Caps lock, Power button, and Lid switch. The system now is stable. No crashes, hangs or hickups whatsoever since. Still no speaker sound and no suspend though. But it seems to get ready for take-off: [https://lists.launchpad.net/ac100/msg00248.html](https://lists.launchpad.net/ac100/msg00248.html)

---

