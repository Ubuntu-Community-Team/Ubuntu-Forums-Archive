---
title: "High System CPU Usage"
date: 2010-10-10
forum: General Help
---

### Post by Blue Matt0 on 2010-10-10
After upgrading to 10.10, my i7 Desktop has become quite slow.
It appears that something in the kernel is using quite a bit of CPU. top shows between 30 and 40%sy, with no processes using over 3% individually, and only 3 or 4 processes using more than 1%.
mpstat shows similar results under %sys (ie not under any interrupt handlers).
As far as I can tell there is nothing in syslog or dmesg that could indicate a problem.

I'm not sure if it could be related, but my computer occasionally boots to only a screen saying "Nvidia Beta Driver" and never continues.  As far as I can tell this screen always flashes when X initializes, but usually disappears.  I have a feeling it is just the other issue eating all my CPU and preventing the Nvidia Driver from initializing.  

Note that the 30-40% CPU makes animated images lag, audio stutter and often freeze while I type, causing the computer to miss several words.

Core i7-920 Overclocked to 4.0GHz
Nvidia GTX 260
10.10 Upgrade from 10.04 x86_64

---

### Post by cap10Ibraim on 2010-10-10
if you still have the old kernel try uninstalling the new kernel and use the older one just to test if it's a kernel issue

---

### Post by Blue Matt0 on 2010-10-10
I do have one, but whenever I try to boot it, it never gets past the splash screen, so I guess the answer is no, I don't have an old kernel.

---

### Post by Blue Matt0 on 2010-10-10
Is there a program that might allow me to see which modules/parts of the kernel are using the most cpu, or is there really any way to go about debugging this at all?

---

### Post by Blue Matt0 on 2010-10-10
For the record, I still see this problem after removing the Nvidia drivers and rebooting.

---

### Post by efflandt on 2010-10-10
There was someone who had an issue with an i7 in the RC which he resolved.  But I did not reply to that post, so I do not know how to find it (a forum search for i7 comes up empty).

It did lead me to install **htop** which gives an ascii graphic representation of what your cores are doing.  But I have had no issues with i5 650 3.2 GHz w/nvidia GT 220 video (10.10 beta from scratch upgraded to RC which after updates is probably current).

---

### Post by Blue Matt0 on 2010-10-12
This issue occurs on my system with the livecd, as well as after a full reinstall with the latest updates.
Both with proprietary Nvidia Drivers and with them removed.

Intel Core i7 920 - Overclocked to 4 GHz
EVGA X58 SLI LE
Nvidia Gefore GTX 260 x2
4x2GB DDR3 RAM
Alfa Wireless-G (Realtek RTL 8187)
USB Audio

---

### Post by hnfmr on 2010-10-13
I'm having the same issue. 10.10 seems to be a lot slower than 10.04 and utilizes far more CPU.

i7 920
nVidia GTS 240

---

