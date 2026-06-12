---
title: "Problems with installing drivers"
date: 2010-11-25
forum: General Help
---

### Post by Petabyte_X1024 on 2010-11-25
Okay, I did my 3rd attempt @ installin' Ubuntu and I've decided to look for help now. 

Problem: When I install Ubuntu, everything works fine and perfect the  effects, ccsm, everything. But this stupid box comes up "proprietary  drivers missing"; I install the Nvidia driver and when I reboot, my  screen goes black and nothing happens. And when I press the power button  the screen suddenly pops up and it starts loading, but I pressed the  power button therefore turning the computer off. I have a  IntelHD GPU  1600MB of VRAM and Nvidia Optimus drivers power it. Should I just ignore  the stupid dialog box?? Because everything works fine, ccsm,  everything. I installed this with Wubi btw.

---

### Post by Bill magee on 2010-11-27
Linux systems cannot access Nvidia cards running under Nvidia Optimus hybrid-switching software. There is currently no solution, sorry!

Uninstall the Nvidia driver and/or remove the /etc/X11/xorg.conf file and run your machine off the onboard graphics.

---

