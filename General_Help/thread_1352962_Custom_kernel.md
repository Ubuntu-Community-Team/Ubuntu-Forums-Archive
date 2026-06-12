---
title: "Custom kernel"
date: 2009-12-12
forum: General Help
---

### Post by blazemore on 2009-12-12
I am familiar with the process of compiling a kernel.
However, I'm always unsure when disabling things, in case I need them.
How can I get a custom kernel that is perfectly tuned to my hardware?

---

### Post by anoovis on 2009-12-12
you can use the "make oldconfig" command google it for the tutorial

---

### Post by blazemore on 2009-12-12
Yes that will give me the vanilla Ubuntu kernel. I want to strip out all the stuff I don't use but how do I know if I use it or not? For example Mac device drivers and Amateur Radio.

---

### Post by buntunub on 2009-12-12
I have not recompiled a Ubuntu kernel before, but I have compiled many vanilla kernals in gentoo and archlinux. The process is extremely easy SO LONG as you know what you need/dont need beforehand. Use tools like lspci, lsusb, etc. to find out what hardware you have (if you dont already know), and when you get to the custom kernel setup stage, then just go in and enable those things and ensure that nothing else is set, then finish the process, reboot with your new kernel, and life is all good. Simple as that. I think it took me like 15 - 20 minutes tops.

Dont forget to setup your GRUB to boot with the new kernel as well.

---

### Post by anoovis on 2009-12-13
for selection u need to read more, understand every options

---

### Post by 3Miro on 2009-12-13
I am not sure you need to remove "everything" that you don't need. If it only takes a few KB of RAM and/or will only load when needed, would it really matter if you leave it in.

I have two laptops and a desktop and everything is running on custom kernels, the most useful part of the settings (IMHO) is the CPU thing. Don't use the "generic" thins and replace it with whatever CPU family you have. Then on an Intel CPU, remove all the AMD crap, and on an AMD CPU, remove the Intel waste. You can also play with the scheduling algorithms (server or low latency desktop).

Afterwards I remove the Battery and AC ACPI options on the desktop, the Bluethoot stuff from the machines that don't have it, the amateur radio that I don't even know why is in the kernel in the first place. Removing the wireless from the kernel causes it not to compile, I am sure it can be fixed, but it wasn't worth the time (on the desktop I don't need wireless). 

Another thing to remove is the debugging symbols, I cannot debug the kernel and no one will really help me with a custom kernel that they have no way to figure out how I messed up. On karmic, you will have to manually edit one of the make files.

You can also remove some of the partition support (such as Amiga and Solaris partitions, I am sure only very few people use those). Be careful, however, once I removed the support for the partition that the kernel needed to boot.

With just a little bit I can get about 8% improvement of speed on the applications that I am running.

---

