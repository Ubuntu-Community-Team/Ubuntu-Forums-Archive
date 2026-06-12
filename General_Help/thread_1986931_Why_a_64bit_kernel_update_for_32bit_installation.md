---
title: "Why a 64bit kernel update for 32bit installation?"
date: 2012-05-25
forum: General Help
---

### Post by gaines2166 on 2012-05-25
I installed 32bit Xubuntu fresh shortly after release, and I have been updating each time I'm notified.  A day or so ago I was presented with recommended updates, which included "Linux kernel headers for version 3.2.0 on 64 bit x86 SMP" and "Linux kernel image for version 3.2.0 on 64 bit x86 SMP."

I knew I had installed 32bit and I only have 2GiB of RAM, so I didn't install them.  Then I noticed that the update message symbol on the panel had an exclamation point, so I let update install them.

Now I see in Synaptic that I no longer have 32bit headers and image, only the 64bit.

Is this normal?  Am I better or worse off?

From System Monitor:
Release 12.04 (precise) 32-bit
Kernel Linux 3.2.0-24-generic
GNOME 3.4.1
Intel® Core™2 Duo CPU E4600 @ 2.40GHz × 2

---

### Post by PhantomTurtle on 2012-05-25
This has to do with with PAE(Physical Address Extension). Your question was also asked at askubuntu ([http://askubuntu.com/questions/140616/updater-offers-linux-kernel-headers-3-2-0-for-version-64-bit-x86-smp-for-my-32](http://askubuntu.com/questions/140616/updater-offers-linux-kernel-headers-3-2-0-for-version-64-bit-x86-smp-for-my-32)).
> Check whether your OS is with PAE extension.

[QUOTE]A 32-bit computer has a word size of 32 bits, this limits the memory theoretically to 4GB. This barrier has been extended through the use of 'Physical Address Extension' (or PAE) which increases the limit to 64GB although the memory access above 4GB will be slightly slower.

Most dekstop/laptop processor made in past 10 year support PAE.

Since Ubuntu 10.04 and newer support PAE out of the box so it can access 64 address line.In 12.04 its default.

Probably that's why you got that kernel image. 64bit means its capable of 64bit address handling, the kernel image architecture is x86 which points that it is for 32bit system.

Unless you have modified your kernel or using the kernel for system software development,its safe to install kernels provide via update-manager.[/QUOTE]

(Answer by user, Web-E)
So yes, it is fine to install and you should have the PAE kernel since it is the default kernel now.

---

### Post by gaines2166 on 2012-05-25
Thanks for the quick reply, PhantomTurtle!

I spent a half hour googling and searching the Forum, but I missed that post you referenced.

Now I can relax!

---

