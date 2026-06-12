---
title: "3D acceleration sometimes crashes"
date: 2010-06-25
forum: General Help
---

### Post by Zeemvel on 2010-06-25
Sometimes if I start a program using OpenGL hardware acceleration, Ubuntu freezes. Both with OpenGL started by a Java application, and with a SDL application, basically anything that uses hardware acceleration.

It doesn't always happen, for example not after a fresh reboot. Maybe after being standby for a night?

I think this started happening since an ubuntu update of one or two weeks ago, which updated the Nvidia driver version.

My system: Nvidia card GeForce GTX 285, Ubuntu 10.4, and using KDE 3.5 Trinity.

Also, sometimes there is a flashing horizontal black bar visible on the two screens at once.

These crashes are very annoying! What could be the cause?

---

### Post by VH-BIL on 2010-06-25
I had a freeze problem using 3D and it ended up being a hardware configuration issue. After spending thousands on replacement parts and technicians it was just the case of the graphics card having to be moved from the top PCI Express slot to the second. I don't know if this is your problem but it may be worth a look.

Trust me, I know how annoying this can be!!!

---

### Post by Zeemvel on 2010-06-25
> **VH-BIL said:**
> I had a freeze problem using 3D and it ended up being a hardware configuration issue. After spending thousands on replacement parts and technicians it was just the case of the graphics card having to be moved from the top PCI Express slot to the second. I don't know if this is your problem but it may be worth a look.

Trust me, I know how annoying this can be!!!

It could be. But it's so hard to reproduce because it happens "sometimes".

Why did the card have to be moved to another PCI Express slot? Does it make a difference?

The horizontal black bars however are something I've also seen on someone else's PC here. Sometimes when starting a program, even if not related to 3D, a black horizontal bar flickers on the screen.

On my PC these black bars sometimes happen right before such a freeze...

I've also had issues before the nvidia driver upgrade I mentioned above. Ever since I upgraded from Ubuntu 9.10 to 10.4 I've had some instability issues, such as KDE4 sometimes suddenly giving a message that the desktop effects (which happen to also use the NVidia card) were slow and got disabled (and then I had to reset the PC anyway because everything responded slowly).

---

### Post by VH-BIL on 2010-06-25
> **Zeemvel said:**
> It could be. But it's so hard to reproduce because it happens "sometimes".
This is why it cost me so much money.!

> **Zeemvel said:**
> Why did the card have to be moved to another PCI Express slot? Does it make a difference?
I do not know, It annoyed me to find out that is all it took after I spent so much much money replacing parts and repairs!

> **Zeemvel said:**
> I've also had issues before the nvidia driver upgrade I mentioned above. Ever since I upgraded from Ubuntu 9.10 to 10.4 I've had some instability issues, such as KDE4 sometimes suddenly giving a message that the desktop effects (which happen to also use the NVidia card) were slow and got disabled (and then I had to reset the PC anyway because everything responded slowly).
I am running the new NVIDIA-Linux-x86-256.35 driver from nVidia. You can try this first if you like. To install it you can use these tutorials:

Install nvidia drivers:
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

Fix the plymouth boot screen for the new nvidia driver:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by Zeemvel on 2010-06-25
> **VH-BIL said:**
> 
Fix the plymouth boot screen for the new nvidia driver:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Hmm, I don't really care what the plymouth logo looks like, BUT, this plymouth process ALWAYS shows up if I type "top", and is ALWAYS consuming a considerable part of the CPU!

Could that have something to do with my crashes, and if so, how can I get rid of plymouth? I find a stable system more important than the looks of a startup logo!

---

### Post by VH-BIL on 2010-06-25
I doubt plymouth is causing the crashes... I was just giving you the option if fixing it if it is displaying as text and not graphic. When I installed the drivers the graphical plymouth stopped but still in text and had fix it.

---

