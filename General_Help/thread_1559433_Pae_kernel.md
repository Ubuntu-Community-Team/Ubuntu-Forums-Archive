---
title: "Pae kernel"
date: 2010-08-23
forum: General Help
---

### Post by jp351 on 2010-08-23
ok, so, i am currently running 9.10 ubuntu (gnome). i have a dual core intel chip at 3.00 ghz. my mobo is an ASUS P5ND2-SLI. my mobo will support up to 8gb of ram. now, as we all know, 32-bit os/kernel will only support like 3.2gb, and 64-bit like 4gb. i'd like to install a pae kernel so i can get the most from my mobo, but honestly, i don't have a clue where to start looking for a pae kernel. i'd like to be able to select it from the list that already appears after the grub loads, and if i like it, be able to remove the rest from the list, or just make it default. i normally wouldn't have much of a problem with running a 64-bit kernel, but again, if my mobo will support 8gb of ram, i might as well get what i can from it as opposed to being limited by software or what have you. question..... in CPU-G, it says my architecture is i686... i don't know if that's the os/distro, or the kernel itself. it also lists the GCC version as 4.4.1 and Xorg as 1.6.4. my current kernel is Linux 2.6.31-22-generic.

again, i'm trying to find a pae kernel, but i don't know if my os/distro will make a difference, if the architecture is the kernel or os itself.. i am still fairly new to ubuntu, and i must say, i've made the switch completely from windows.. which blows...

....can anyone point me in the right direction??? 
thanks :)

---

### Post by amauk on 2010-08-23
If your machine is 64bit,
just use the 64bit version of Ubuntu

64bit systems can address up to 256 Terra-bytes
so your 8GB of ram is no problem

PAE is only really for older systems that are not 64bit capable

---

### Post by jp351 on 2010-08-23
i was under the impression that 64-bit will only address up to about 4gb of ram, and that there were still a few minor compatibility issues with certain progs and 64-bit os/kernels

*edit*
i just want to update/upgrade/modify my kernel so that i can use more than the 3.2gb of ram addressable by 32-bit.. if i install a 64-bit kernel, will i have to modify/install a new os??? i've got my computer set up EXACTLY the way i want it, i just want to be able to use/have access to more ram..

---

### Post by amauk on 2010-08-23
x86_64 can theoretically address up to 16 Exa-Bytes (which is 16,000,000,000 GB)

Current generation hardware have a limit on that though, the max today is 256 Terra-Bytes

---

