---
title: "Extra RAM install Question - Slightly Buggy?"
date: 2012-09-04
forum: General Help
---

### Post by Alcidious on 2012-09-04
Howdy folks,

This weekend I added a wireless network card (TP-LINK PCI 300 mbs Adapter)and two extra sticks of RAM (Crucial, 2GB 240-PIN DIMM 256MX64 DDR3PC3-8500 UNBUFF)to my Desktop. The Desktop is a custom build (Note-my friend built it for me while i watched), but I only recently installed Ubuntu [12.04] on it (I've been using Ubuntu solely on my laptop since December, but had Windows on Desktop previously). 

The motherboard is an Intel Desktop Board DX58SO with an Intel Core i7 processor and an XFX ATI graphics card. I installed the wifi card and the two sticks of Ram; while the wifi card is working wonderfully, I think the RAM is causing my system to be a bit buggy.

For instance, the screen will "pause" for a few seconds occasionally, and then continue on (like if i begin typing, it won't show up at first, then after 5-10 seconds all of what I typed will).  Here is my question:

I tried to get the very same ram as before, but the model number is slightly different ( I need to pull it out to see exact difference, did write down but lost). Could this be the problem? They are all DDR3... 

OR 

Is it the available slots on the Motherboard? There are four slots so I assumed four sticks of RAM was best...but when I installed them I noticed the following: 

-Channel A, DIMM 1 (it's Black)
-Channel A, DIMM 0  (the rest are blue)
-Channel B, DIMM 0
-Channel C, DIMM 0

What is the difference between DIMM 1 and DIMM 0? I did a google search and saw really poor answers... I apologize for length, however I'm trying to learn as much as possible and I wanted to be thorough.  Thanks everyone for putting up with me!

---

### Post by sandyd on 2012-09-04
Have you run memtest on the RAM sticks?

---

### Post by Alcidious on 2012-09-04
no, how do I do that?

---

### Post by sandyd on 2012-09-04
You can download memtest from [http://www.memtest.org/](http://www.memtest.org/) , or just use the version on the livecd.

If you press ESC while booting from the livecd, the boot menu will appear, and you can select memtest.

---

### Post by Cheesemill on 2012-09-04
No need to download anything, it's already included with Ubuntu.

Just select memtest from the GRUB menu when you boot.

---

### Post by Alcidious on 2012-09-11
So I'm not seeing the GRUB menu when I boot.  I only have ubuntu 12.04 on my hard drive, and I haven't downloaded any other kernels or anything.

Last night I changed the /etc/default/grub to show GRUB_TIMEOUT=2 to GRUB_TIMEOUT=15, and yet I still don't see it. Any ideas on what to do, or how to get there to perform memtest?

Sorry I slacked on my own thread, been a hectic couple of weeks.

---

