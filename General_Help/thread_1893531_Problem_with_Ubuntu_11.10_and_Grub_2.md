---
title: "Problem with Ubuntu 11.10 and Grub 2"
date: 2011-12-10
forum: General Help
---

### Post by ShayanH on 2011-12-10
Hi there!
I installed Ubuntu 11.10. When I turn on the PC and grub 2 started, grub doesn't show and I see in my monitor:
Out of range. 98kHz / 58Hz
Until now I can't solve this problem.
My system properties:
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
Memory (RAM): 2.00 GB
Graphics: NVIDIA GeForce 6150SE nForce 430
Mother Board: GeForce6100PM-M2
Monitor: LG E1940S
*I installed Graphics driver.

---

### Post by zvacet on 2011-12-10
Read [this.]("https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution")

---

### Post by Alln on 2012-01-05
Hi! :)

I have a GeForce 6150SE nForce 430, and I had this problem too, but was solved after setting gfxmode in /etc/default/grub

In my case, I have a 19" TV-Monitor, and the full resolution is 1360x768

I've set up gfxmode=1024x768 to grub, and I installed nvidia graphics driver (290.10)

But, the X give me only a black screen! :confused: Can you, please, explain the steps you followed to install and configure in Ubuntu 11.10?

Thanks!

---

### Post by Renewable on 2012-01-08
thanks zvacet, but i already tried the part about adding undetected resolutions. Here is my output: 
$ cvt 1920 1200

$ 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync


$ xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
xrandr: Failed to get size of gamma for output default

---

