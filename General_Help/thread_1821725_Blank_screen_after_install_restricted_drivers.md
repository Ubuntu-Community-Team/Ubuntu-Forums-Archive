---
title: "Blank screen after install restricted drivers"
date: 2011-08-09
forum: General Help
---

### Post by supermario641996 on 2011-08-09
I just reseantly got an Asus Essentio CM1730-05 desktop and I installed Ubuntu 11.04 on it with Wubi. After doing so, I installed the restricted driver for my onboard ATI Radeon 3000 graphics. After doing so I get to a blank screen right after the splash screen. Also I think it is frozen because I don't here the Log in music and I have to hard reboot instead of just hitting the power button. If you need to know more about my hardware just ask. Also I have tried two different monitors. A Dell M991 and my HDTV. I have used the following hook ups to the HDTV-DVI to HDMI and HDMI to HDMI. The Dell M991 is like any older monitor. Just that one VGA hook up. Anyway. I would really aprietiate the help and I noticed there is an Asus section so I hope that this is still the right spot. I have tried the following.
Replace quiet splash with nomodeset and also i915.modeset=1. I have yet to try i915.modeset=0.

---

### Post by Mark Phelps on 2011-08-09
Ubuntu 11.04 takes a LONG time to boot to the desktop -- much longer than any previous version I've used.  

The sequence I see is the following:
1) Ubuntu and red dots
2) Blank screen -- dark grey, not black
3) Long wait with lots of disk activity (while the screen is blank)
4) Sudden shift to Black screen (no longer dark grey) -- but still blank
5) Another long wait, and more disk activity
6) Finally (after several MINUTES), the logon screen.

So, let it go for a while and see if you get the same sequence.

---

### Post by supermario641996 on 2011-08-09
Hey thanks for your reaply but this didn't work.  I don't get a dark grey screen.  I get a black screen.  Also there is no Disk activity while this is happening.  Ubuntu also boots quite fast without the Restricted driver installed.  I am going to do a fresh install with Wubi again and see what I can do.  There was only one restricted driver to pick and I am not sure if it said recomended or not.  Thanks again for your reaply.

---

### Post by .... on 2011-08-09
I would not recommend installing the restricted driver if you don't need it. If you must, follow this: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)

> I have tried the following.
Replace quiet splash with nomodeset and also i915.modeset=1. I have yet to try i915.modeset=0.
Those boot switches are for Intel graphics. They won't do anything on an ATI system.

---

### Post by supermario641996 on 2011-08-09
Well I solved my problem.  Anyway.  If you have the same problem as me.   Update Ubuntu 11.04 with the update manager then install the proprietary drivers.  Thanks for the help but I guess I figured it out.

---

