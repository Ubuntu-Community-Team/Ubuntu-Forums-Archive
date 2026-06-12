---
title: "Finding Installations of Ubuntu on cpu"
date: 2010-06-23
forum: General Help
---

### Post by zacharyrs on 2010-06-23
Hi I have just installed BURG which is awesome - allows me to boot into either U!, Win (shutter) or whatever OS I have on the cpu.

However when I go into boot it has 4 different types of Ubuntu and I'm confused why I don't just have one single Ubuntu OS. Is there a way to see how many I have installed once I'm logged into Ubuntu so I can try to figure out why I have so many and what the differences are - so I can hopefully work my way down to one Ubuntu to pick from when booting?

---

### Post by ajgreeny on 2010-06-23
You probably only have one ubuntu installed but the menu is showing different kernel versions, eg 2.6.32-21 and 2.6.32-22, and there will also be recovery mode versions of both for you, ie 4 choices.

This is quite normal and I would suggest you forget it and just boot to the default, which is the latest.  I always the previous kernel version on my machine, even when I know the latest works OK as it is possible for kernels to simply not boot sometimes, and it is good to have an alternative.  If more than two versions are available I usually uninstall the oldest with synaptic, just to leave the two.  That removes that menu entry from grub, so I imagine it will do the same in burg.

---

### Post by zacharyrs on 2010-06-23
Ty so much for your reply.

To install a kernal what exactly would I look for in Synaptic?

When you say a kernal may not boot for whatever reason, would this mean that kernal would then have to be removed (no chance of it working again at a later period)?

---

### Post by ajgreeny on 2010-06-23
> **zacharyrs said:**
> Ty so much for your reply.

To install a kernal what exactly would I look for in Synaptic?

When you say a kernal may not boot for whatever reason, would this mean that kernal would then have to be removed (no chance of it working again at a later period)?
Any new kernel will be notified in update manager so no need to worry about installing.  To uninstall an unwanted older one search in synaptic for the number ie **2.6.32-21**, using the name only search filter, and all the packages with that number will appear, the kernel and other additional packages, which you can remove.

If a kernel has stopped working for whatever reason, you can use the **remove completely** in synaptic and then re-install it if you wish.  Don't forget, you should not remove the kernel that you are actually using or you're in big trouble..

---

