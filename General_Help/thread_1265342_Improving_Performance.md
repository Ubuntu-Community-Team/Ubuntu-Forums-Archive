---
title: "Improving Performance"
date: 2009-09-13
forum: General Help
---

### Post by Enk on 2009-09-13
Hi

I am on a quest to improve the performance of my laptop, and seek your assistance! 

**The goal**
I want to be able to smoothly use Blender and GIMP on my laptop. I also want to improve the overall performance of the laptop (everything from faster boot, opening of programs, etc)

**The computer**
I am running Ubuntu 9.10 fresh installed. I'd used Xubuntu 9.04 for some time, but something made my computer lock from time to time after a few months.

CPU: AMD Sempron SI-40, 2GHz
RAM: 2GB (2x DIMM DRAM Synchronous 667 MHz)
Graphic Card: GeForce 8200M G

**Current actions**
I have disabled (and uninstalled) compiz. I use Firefox as primary browser (with the flashblock addon), and do not have any other addons active.  

Also I am using ext4 on my file system.

**Issues**
In Blender I've notices some performance issues (I am not sure if this actually is because of performance though). I notices that if I select an object/vertex/edge/face and press the shortcuts to translate/rotate/scale, then there is a small delay (100-500ms maybe) before I can move the mouse to perform the transformation.

Weight painting bones is also very "sluggish".


**All tips welcome**
As long as it doesn't destroy my laptop :)

One question I have is if I use the best graphic card driver for my card? Currently I am using the Nvidia accelerated graphics driver v185.

---

### Post by Enk on 2009-09-13
I've just checked if my CPU supports 64-bit operating mode, and apperently it does :O
(the laptop came with vista x86 so I haven't considered it before). 

"cat /proc/cpuinfo | grep lm" does at least give me "flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp **lm** 3dnowext 3dnow constant_tsc up nonstop_tsc extd_apicid pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch osvw skinit" 

Will changing to Ubuntu x64 give any performance improvement?

---

### Post by NoaHall on 2009-09-13
1)Performance wise, it's not a good idea to be using a alpha OS. Change back to 8.04 or 9.04

2) Try using lxde instead of xfce. It's more lightweight.

3) Make sure the latest drivers are up to date

4) Recompile Blender from source

5) Blacklist some things that you don't need.

6) sudo apt-get install preload

7) Yes, ubuntu 64 is better always, but I've heard someone had a problem when forcing Blender 32 bit to install under it

---

### Post by Enk on 2009-09-13
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

This benchmark did at least look promising :)

Guess I'll give Ubuntu 9.04 64-bit a try. And wait for the 9.10 release before I upgrade :)

---

