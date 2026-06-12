---
title: "nvidia stopped working (after hibernation?)"
date: 2005-03-12
forum: General Help
---

### Post by djst on 2005-03-12
I was successfully running xorg with the "nvidia" driver before on the latest Hoary preview release. Yesterday, I tried the [System > Log Off > Hibernate] feature in Gnome and all that happened was that my monitor was shut down and all other hardware went to sleep. I couldn't do anything to wake the computer up, so I hard rebooted.

After that, the nvidia driver won't load for some reason, with the following output:
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xF0000000
(--) NVIDIA(0): MMIO registers at 0xF9000000
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

I have tried reinstalling nvidia-kernel-common and nvidia-glx from Synaptic, and even tried the nvidia-kernel-source, but no luck. Running lsmod doesn't display the nvidia module at all.

Any ideas?  :-(

Oh, and if I edit xorg.conf and replace "nvidia" with just "nv", xorg runs again, but obviously I want to use the much faster nvidia driver.

---

### Post by c_dog on 2005-03-12
The new Hoary 2.6.10-6 (26) kernels for AMD64 & i386 from yesterday quit taking the 6629 glx driver on my multi-boot (SuSE 9.2 x86_64, SuSE 9.2 i386, Ubuntu Hoary AMD64, Ubuntu Hoary i386, & WinXP 64) Asus A8N SLI Deluxe w/ 6600GT & dual LCDs. I was able to get nvidia's AMD64 7167 script to run with little effort on the 64bit Linux's, but for some reason the i386 7167 script wouldn't accept the 2.6.10 kernel source would work with the 2.6.10-6 (26) kernel. After a little looking around, I found these  [http://retroject.net/nvidia/](http://retroject.net/nvidia/)   They've been working just fine with Hoary's 2.6.10-6 (26) and now 2.6.10-6 (27). 7167 has got glxgears going over 7000 fps on a single 6600GT. That's a few hundred fps better than 6629. 

c_dog

---

### Post by djst on 2005-03-24
The problem is solved. Appearantly, you can't just install any kernel version in Ubuntu and expect the nvidia driver to work. It seems you must install the linux-restricted-modules package for the kernel you've installed.

For example, I solved the problem by installing the kernel called linux-image-2.6.10-5-686-smp with the corresponding linux-restricted-modules-2.6.10-5-686-smp package and I was able to use the nvidia driver then.

---

### Post by Leif on 2005-03-26
Cheers ! I'd been trying to figure this one out for quite a while. restricted-modules. Wouldn't have occurred to me in a million years.

---

