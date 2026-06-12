---
title: "Xorg hang-up"
date: 2010-12-09
forum: General Help
---

### Post by menthos on 2010-12-09
Hallo gals and guys

First of all: Hello! I'm new tot is forum and this is my first post, so have a bit patience with me.


Alright to my problem:
I searched around for over a days but somehow i don't seem to be able to solve it. If I start my laptop with the xorg.conf file it will freeze and it seems as if xorg is hung up. I switched to console, logged in, stopped the gdm and start Xorg manually from there. The same thing happens. If I check my xorg.conf file now there are no errors. It just seems to hang up somewhere.
If i remove my xorg.conf file now and start the gdm again, X starts normally. However, like this i do not have any visual effects.

My system (or at least whats interesting):
GPU 1: nvidia corporation GT216 (GeForce GT 330M) PCI 01:00.0
GPU 2: Intel Corporation Core Processor Integrated Graphics Controller PCI 00:02.0
OS: Ubuntu 64 bit 10.10

What i have done until now:
Installed the nvidia driver from the official homepage.
Generated the xorg file with nvidia-xconfig
Generated the xorg file with dpk-reconfigure xserver-xorg (which didn't work at all!)
Added the "DPF" option to the xorg.xonf file (which had no effect)
blacklisted all other drivers except the nvidia (strangely with no xorg.conf file i can still log in and everything works, even if i have the modules blocked.)

The xorg.conf and Xorg.0.log files are both attached to the post.

I really don't now what to do. Maybe someone has an answer to my problem.


Thanks in advance for helping me.

Have a nice day!
Menthos

---

