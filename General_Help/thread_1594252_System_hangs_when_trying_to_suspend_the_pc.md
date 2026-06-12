---
title: "System hangs when trying to suspend the pc"
date: 2010-10-12
forum: General Help
---

### Post by ami7878 on 2010-10-12
I'm using a Toshiba satellite U400 and just upgraded from 10.04 LTS to 10.10  and now, every time I try to suspend the PC, it hangs.  Before, 10.04 LTS worked  perfectly.

I searched ad could only find some talks about 'vt switch' ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/604252](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/604252)) but couldn't understand if there is a solution to the problem and if yes what is it :confused:

This is really frustrating.

---

### Post by ami7878 on 2010-10-14
Isn't there anyone that have anything to say about this so I wouldn't feel like I'm all alone. 

Up to 10.10 I was enjoying my Ubuntu but it seams like someone was to hasty releasing a "perfect" 10 system on October 10 and now I cannot leave my pc open cause when, after a while, it tries to go to sleep (suspend mode) it freezes and I loose all my work :mad:

---

### Post by gatman3 on 2010-10-14
Just so you don't feel so alone... I'm experiencing suspend-to-RAM hangs with 10.10 on my Lenovo W500.  Just starting to research; I'll post back.

---

### Post by gatman3 on 2010-10-15
Still researching.  Seems like many are experiencing this problem with 10.10, and there may be different issues affecting different machines.

The most useful info I have found thus far provides a workaround of sorts.  The suggestion was to install acpitool:

```
sudo apt-get install acpitool
```

and then try suspending using acpitool:

```
sudo acpitool -s
```

This works for me.  Suspend-to-RAM when shutting the laptop lid still hangs, but I can at least suspend successfully with this command line now.

In the meantime I guess we're waiting for an update to get pushed out to fix this.  I'll post if I find a better workaround.

---

### Post by ami7878 on 2010-10-15
Unfortunately this didn't work for me or maybe I'm doing it wrong.

I've installed the acpitool as you suggested and run the "sudo acpitool -s" command from the terminal (I tried both from the gnome terminal and the tty: Alt+Ctrl+F1).  I got some messages saying the system is suspended but that's it :confused: 

The only way to exit this state was to power off the pc.  When I tried to return to the gnome (Alt+Ctrl+F7) the pc freezes.

---

### Post by gatman3 on 2010-10-15
Well, unfortunately I'm not real surprised.  I still haven't had a ton of time to research this, but it sounds like there may be multiple problems out there.  I have seen references to speculation that the suspend problems in 10.10 relate to USB3, Nvidia graphics, bluetooth or even the 2.6.35 kernel in general.  Since we are running different hardware (Toshiba vs Lenovo) you may very well have a different problem.  I looked up the specs on your U400 and it looks like about the only thing we have in common is intel graphics.

Hopefully this gains some more attention by the developers and they get some fixes pushed out very soon.  I'm always frustrated when the latest Ubuntu release goes backward in some key way with respect to the previous release.

I'm subscribed to your thread now; I'll post more if I learn more.  Good luck.

---

### Post by ghsfr33d0m on 2010-10-21
Both mine and my girlfriend's Lenovo laptops have had troubles like this off-and-on for the last few Ubuntu distros. I got mine working on 10.04 by turning Compiz on, I was then able to turn it off and suspend kept working. You can try that if you want by right clicking on the desktop -> change desktop background -> visual effects -> extra. As I understand it, that turns Compiz on. 10.10 did not break suspend for me, but it didn't fix it for my girlfriend either. I'll post back when I fix hers, but that may be on the order of weeks, as I get some time.

ghsfr33d0m

---

### Post by Burfee on 2010-10-28
same problem for me on my dell studio xps and on my desktop also. it used to work on ubuntu 10.04 and not it's really annoying...

---

### Post by franciscoam on 2010-12-01
I'm experiencing the same problem on my Asus Eee PC 1001HA + Kingston V 64GB SSD and 2GB of ram (original is 1GB). It's really annoying... i've lost some work after successive hangs in just two days using Ubuntu 10.10...

---

### Post by hoesterholt on 2010-12-08
I'm experiencing the same problem with my HP 2710 tablet laptop. My laptop worked perfectly with 10.04, but now with 10.10 I get random hangs on sleep (I never suspend). About every 5 sleeps the system hangs and needs to be rebooted. Annoying, because I work during traveling a lot and need to put my laptop in sleep mode often.

---

### Post by franciscoam on 2010-12-08
I've configured my eee pc 1001HA to never sleep. It just suspends after a certain time and hibernates on very low battery level. This configuration apparently solved the crash problem. I've also just installed kernel 2.6.36 ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.36-maverick/")) and I hope it can fix the issue, but I didn't tested yet.

---

### Post by ami7878 on 2011-01-03
Installing 2.6.36 has solved the suspend issue for me. I'm smiling again :p

---

