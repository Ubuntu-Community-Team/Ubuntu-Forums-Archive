---
title: "Some problems I've been having with 10.04(Ub and Kub)"
date: 2010-05-03
forum: General Help
---

### Post by swalker23 on 2010-05-03
I've been trying Ubuntu and Kubuntu 10.04 past few days and encountered the same problems in both of them.  My problems are when I reboot,shut down, log off, and hit ctrl+alt+(F1 or F2)I hear a series of beeps from my mobo and then my monitor goes into shut down.  All this starts after I install the nvidia drivers either by hardware drivers or manually.  I will list what I do when I encounter the problems from either fresh install or upgrade.
1. Install Ubuntu or Kubuntu and everything is fine.
2. Log in and everything is ok besides the splash before log in.
3. Install nvidia drivers(everything ok) and reboots fine.
4. After the install of the drivers when I reboot, shut down, ctrl+alt+F1
   and ect I get the black screen but no beeps.  I have to shutdown via
```
sudo shutdown -r now
In ubuntu it shutdowns but in kubuntu it reboots
```
```
sudo halt
in kubuntu it shutdowns
```
5. I follow the guide to fix Plymouth from [http://ubuntuforums.org/showthread.php?t=1469475]("http://ubuntuforums.org/showthread.php?t=1469475")
   After I do that and reboot, shutdown, and etc thats when I get the series of beeps.  Its like 4-6 beeps.

I just want some solutions on how to fix it, I've tried several things from post to post but nothing seems to work.  I also want to see if anyone else experiencing these problems.  I also forgot to mention that in Ubuntu after I ran the code (sudo shutdown -r now) and after the power down I turned my PC on and Ubuntu shutdown like it suppose to on the task bar but with the beeps.  In Kubuntu I have yet to see this happen.

My system specs: EVGA E759 Classified, 2 x 285GTX in sli, and a 9800GT for a physx card.

---

### Post by wojox on 2010-05-03
Sometimes beeps are a way of telling you something is about to go hardware wise. What if you just opened your desktop terminal and ran those commands?

sudo shutdown -r now
In ubuntu it shutdowns but in kubuntu it reboots

-r is reboot. that's strange.

---

### Post by swalker23 on 2010-05-03
> **wojox said:**
> Sometimes beeps are a way of telling you something is about to go hardware wise. What if you just opened your desktop terminal and ran those commands?

sudo shutdown -r now
In ubuntu it shutdowns but in kubuntu it reboots

-r is reboot. that's strange.

I'm pretty sure nothing is wrong with my hardware, but it might something that conflicting with the SLI setup and the 9800gt.  Everything was working fine in Karmic few days ago and everything was fine before installing the drivers and fixing plymouth.  I ran those in the desktop terminal.  It is strange that in one it shutsdown but in the other reboots.  I can deal with it now but I would love to get it fixed.

---

### Post by swalker23 on 2010-05-03
So no one else but a very few experiencing this problem?

---

