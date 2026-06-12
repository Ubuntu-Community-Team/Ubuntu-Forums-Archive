---
title: "Intel HD Graphics 3000"
date: 2012-05-01
forum: General Help
---

### Post by GammaScorpii on 2012-05-01
Hi guys, been a while since I've needed help but here goes...

I'm trying to run my integrated Intel HD 3000 graphics with my i7 2600k in 12.04 64-bit, and as it stands I'm stuck in a 1024x768 screen resolution.

There's nothing in the restricted drivers app but I've been told Ubuntu should automatically set Intel's graphics up. Is there somewhere I'm supposed to get the drivers or should I just look on Intel's website?

Cheers.

SOLVED: [http://ubuntuforums.org/showpost.php?p=11901015&postcount=12](http://ubuntuforums.org/showpost.php?p=11901015&postcount=12)
It's possible Ubuntu has an issue with the Gigabyte GA-Z68XP-UD4 motherboard.

---

### Post by Gyokuro on 2012-05-01
Hi

could you please post your /var/log/Xorg.0.log and /var/log/kern.log?

---

### Post by GammaScorpii on 2012-05-02
Sure thing.

Thank you. ;)

---

### Post by GammaScorpii on 2012-05-03
bump

---

### Post by papibe on 2012-05-03
It looks like you have 2 monitors connected, one using a VGA connection and the other using HDMI.

Which one is giving you trouble?

Have you use 'Monitors' to adjust the resolution of the monitors?

Regards.

---

### Post by GammaScorpii on 2012-05-03
That's strange because I only have one monitor, and my motherboard doesn't even have a VGA connection.

This is my motherboard: [http://www.gigabyte.com.au/products/product-page.aspx?pid=3977#ov](http://www.gigabyte.com.au/products/product-page.aspx?pid=3977#ov)

My monitor is indeed connected via the solitary HDMI port though.

---

### Post by papibe on 2012-05-03
Could you post the content of this file?
```
/etc/X11/xorg.conf
```
Regards.

---

### Post by GammaScorpii on 2012-05-03
There doesn't seem to be a xorg.conf file present in X11. Is there something I have to do to generate it?

---

### Post by Dubslow on 2012-05-03
For what it's worth, when I tried to put 10.04 on my laptop (i3-2350M) I got similar resolution limiting, Compiz didn't work right... then it occurred to me that 10.04 predated SB by at least a year. Since I installed 12.04 (testing candidate at the time) my resolution/Compiz have been fine. I imagine anything since 11.04 would work fine.

---

### Post by GammaScorpii on 2012-05-03
That's what I gathered from searching around for the problem. Fact is, I am using 12.04 and everything is updated. Maybe an issue with 64-bit? Maybe an issue with my particular motherboard? Not sure.

---

### Post by Dubslow on 2012-05-03
> **GammaScorpii said:**
> That's what I gathered from searching around for the problem. Fact is, I am using 12.04 and everything is updated. Maybe an issue with 64-bit? Maybe an issue with my particular motherboard? Not sure.

Huh. My laptop couldn't run 64bit USB live discs, but once I got my hands on a DVD everything installed/works just fine.

---

### Post by GammaScorpii on 2012-05-03
BREAKTHROUGH:

[papibe]("http://ubuntuforums.org/member.php?u=774785") was correct in that my system is for some reason detecting two monitors when in fact I only have one. In my "Displays" app, my monitor is labelled as "unknown", BUT, if I uncheck "Mirror Displays", a second display pops up with my correct monitor. If I switch to this display, I can select my correct (full) resolution. When I do this, the monitor switches to the correct resolution, but I can't do anything! I can move my mouse around the screen, but all my windows are hidden, I can't alt-tab, I can't open any applications, etc.

SOLVED:

Had to turn the "unknown" display to OFF. Everything is good now. Thanks for your help guys! :D :D

---

