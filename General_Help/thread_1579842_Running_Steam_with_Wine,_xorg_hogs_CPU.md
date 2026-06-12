---
title: "Running Steam with Wine, xorg hogs CPU"
date: 2010-09-22
forum: General Help
---

### Post by semicomatose on 2010-09-22
Freshly installed and updated Ubuntu 10, the first thing I did was install Wine and the second was installed Steam under Wine. Steam will run, but the moment it opens, xorg's CPU usage jumps to around 70% and stays there.

Help to resolve this?

Graphics card is an old ATI Radeon 9600 pro.

-semi

---

### Post by joshuarowley42 on 2010-09-23
I am actually having exactly the same problem. 

What I wanted to bring to the table is that I ran steam before, and it worked with very acceptable performance. I do note that it seems to be a new version that I am running, so suspect that a recent change has caused these problems?

Seems that Half-Life(1) runs fine, so I am not too bothered! :)

I suspect that my (our) CPU is doing work that should be run on the GPU, what graphics driver version are you using??

I am running the following system:
Ubuntu 10.04 (x86)
wine-1.1.42
AMD64 3000 Dual core
Nvidia GeForce 6800 Ultra (Driver Version 195.36.24)
X.Org X Server 1.7.6
Steam API: v009 16th Sept 2010 build.

---

### Post by semicomatose on 2010-10-04
I'd given up for the moment and reassembled that computer into an Ubuntu server, so I can't get you the exact specs, but here's what I know:

Ubuntu 10.04
ATI Radeon 9600 Pro graphics card
AMD Athlon CPU
wine and Steam are freshly installed, and I don't know what Ubuntu picked for the graphics drivers for that card, but I haven't been able to install proprietary stuff.

-semi

---

### Post by Mark Phelps on 2010-10-04
> **semicomatose said:**
> ... but I haven't been able to install proprietary stuff. 

And you won't ... because those drivers don't exist anymore.  AMD dropped proprietary driver support for your card a long time ago.

You're running the default open-source drivers now, and that's all that is available for your card.

---

