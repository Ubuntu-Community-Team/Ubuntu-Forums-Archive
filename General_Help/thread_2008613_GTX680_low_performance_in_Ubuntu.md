---
title: "GTX680 low performance in Ubuntu"
date: 2012-06-22
forum: General Help
---

### Post by Ishayu on 2012-06-22
Whenever I play games using Wine in Ubuntu on a GTX680 with the latest proprietary drivers, I'm experiencing a weird issue. Basically the card barely heats up at all, and generally stays at around 20-30% usage, causing pretty wretched performance. The drivers are working though on a basic level and simple games play fine. In fact every native game I can think of plays fine, but not because the bug is not present, but rather because they require around 20% of my graphics card's total capacity to run at highest settings (including Oil Rush)

I really am at a complete loss as to what to do or even where to begin addressing this. Has anyone ever experienced something similar or can recommend steps to remedy this issue?

If you need any info from my system, just ask!

I do not have this issue under Windows, however if I triple the performance from my Ubuntu setup (which I should theoretically be able to) then it is quite clear to me that Ubuntu would run significantly better than Windows for nearly all gaming-related tasks.

---

### Post by schtufbox on 2012-06-23
It's not just you.  It just started happening to me too, on both my desktop and laptop.
Things were fine until yesterday, then after some updates I started having the issues you describe.
My desktop is a Quad core q6600 o/c to 3ghz, 4gb memory, geforce GTX 260 (proprietary drivers).  I also put my old Radeon 4850 in too, and had the same issues with the frglx drivers.

My laptop is also doing it, it's a samsung x11 with 2gb memory, intel core 2 duo 1.83ghz and nvidia geforce go 7400 gfx.

I've also noticed that gnome shell occasionally starts getting corrupted graphics too.

---

### Post by Ishayu on 2012-06-23
I haven't actually noticed any terrible bugs of terribleness in terms of graphics glitches. I did a lot with FGLRX though, so nothing new there. It's probably just AMD being AMD again.

But this is just so weird. Like I can go on for example Jake Ward's YouTube channel and watch him play the latest games while recording them in high resolution WITH WORSE SPECS and I really can't get anywhere. The performance is just awful.

---

### Post by Ishayu on 2012-06-24
Bump.

I still need help and I have further info!

The NVIDIA driver sets the performance level to 0 using adaptive clocking.

This means 324 (of 705) MHz graphics clock, 324 (of 3004) MHz Memory clock, and a 648 (of 1411) MHz processor clock.

Under these circumstances World of Warcraft through Wine will give me 30-40 FPS on max settings for OpenGL, but it's slightly spikey. Other games run much worse. Starcraft 2 runs at Fair at 30-40 FPS.

I've tried to change the settings such that the graphics card always goes as nuts as it can, but it simply results in a <10% usage and a heating card!

---

### Post by efflandt on 2012-06-24
Just curious if you are only discussing games in wine or any other Linux graphics?  I don't seem to have any issues in 64-bit 11.10 running nvidia-current 302.17 drivers from xswat repository (actually I probably don't even need xswat).

A java game "minecraft" using openjdk-6-jre runs in the mid-100 to mid-200 or more fps most of the time, not less than about 70+ during initial heavy chunk loading.  Of course @ 1080p it actually only displays 60 Hz.

At that time NVIDIA X Server Settings shows:
Graphics Clock 951
Memory Clock 2178
Processor Clock 1903
Temperature 67C

PS: Not really any noticeable difference running 64-bit 12.04 with nvidia-current 295.40 from USB hard drive.

---

### Post by Ishayu on 2012-06-25
> **efflandt said:**
> Just curious if you are only discussing games in wine or any other Linux graphics?  I don't seem to have any issues in 64-bit 11.10 running nvidia-current 302.17 drivers from xswat repository (actually I probably don't even need xswat).

A java game "minecraft" using openjdk-6-jre runs in the mid-100 to mid-200 or more fps most of the time, not less than about 70+ during initial heavy chunk loading.  Of course @ 1080p it actually only displays 60 Hz.

At that time NVIDIA X Server Settings shows:
Graphics Clock 951
Memory Clock 2178
Processor Clock 1903
Temperature 67C

PS: Not really any noticeable difference running 64-bit 12.04 with nvidia-current 295.40 from USB hard drive.

I've tried both the X-swat repository and manually installing the drivers. The result is completely identical.

Right now I'm playing an HD video (HTML5, Firefox) on YouTube and playing World of Warcraft at 40-50 FPS. My card is throttled down to 540, 810, 1080 (graphics, memory, processor clock).

Fan speed is ~35% and temperature at about 55C. Not an overheating issue.

This happens both in Wine and native games, such as Oil Rush. It doesn't happen in Minecraft because Minecraft somehow manages to specify to go crazy. On top of that Minecraft is not at all a demanding game. My card could probably sleepwalk through it on max settings and several hundred FPS.

---

### Post by Ishayu on 2012-06-27
bump

---

