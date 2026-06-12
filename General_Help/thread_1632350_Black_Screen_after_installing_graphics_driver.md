---
title: "Black Screen after installing graphics driver"
date: 2010-11-27
forum: General Help
---

### Post by NickClyde on 2010-11-27
Hey, just installed 10.10 on my Sony Vaio F laptop. Here's my specs:

Processor: Intel Core i7 720QM (1.6 GHz)
Memory: 6 GB DDR3 (1333 MHZ)
Graphics: NVIDIA GeForce 330M (1 GB VRAM)
Hard Drive: 500 GB (7200 rpm)
Native Resolution: 1920x1080

I shrunk my Windows partition, installed Ubuntu on it's own partition with swap space, and mostly everything went fine. When I booted up, the resolution was set at something like 2048x1536, and it only displayed the top left corner of about 70% of the screen. When I changed to any other resolution, it looked really bad, and the whole screen still wasn't displayed.

Then something popped up telling me to install a driver for my graphics card, so I did, figuring it would fix the problem. When I booted and picked Ubuntu, I was stuck with a black screen. So I restarted and tried booting into safe mode. I got in, and it displayed the whole screen at 800x600. Still no luck in regular mode, however.

Any ideas?

---

### Post by iNsOmNiOuS on 2010-11-27
In Safe mode open up System > Administration > Hardware Drivers and uninstall the Graphics Driver

---

### Post by NickClyde on 2010-11-27
OK, but do you have any ideas about the whole screen not displaying before the driver was installed? I can't see the bottom bar no matter what resolution I set it to, and the only one that looks crisp is 2048x1536.

---

