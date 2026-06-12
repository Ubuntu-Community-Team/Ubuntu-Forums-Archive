---
title: "Please help"
date: 2006-01-26
forum: General Help
---

### Post by TecSoft on 2006-01-26
Hey everyone this is my first post :)!!! Okay anyway I installed Ubuntu 5.10. But when I load it, it says can not show X or whatever. Can anyone help me fix this. I can only boot into console. It tries booting into X but it dosn't work. What can I do? Here is my system.

System
------
Brand and Model: Dell Dimension 2400
Hard Drive: 40 gig (where Ubuntu is) 120 gig (where WinXP is)
RAM: 1 gig
CPU: Intel Pentium 4 2.80ghz
Video Card: BFG Tech nVida GeForce 5500 FX Over Cooled Edition 256 MB RAM PCI Edition

PS 1: I did sudo nano /etc/X11/xorg.conf and I check the device it showed my intergated graphics card (Intel) that I don't use. I use the GeForce/

PS 2: If anyone could help me ASAP that would be great. 

PS 3: If there is anything you need to help me with that I have not provided please let me know.

---

### Post by Qrk on 2006-01-26
type in 

sudo dpkg-reconfigure xserver-xorg

and answer the series of prompts about your monitor and other hardware. The most crucial part is choosing a driver. The reason X didn't work is the default driver probably didn't work (it should be nv)... try one that is less optimized but works with more hardware, like vesa or vga. Once in a graphical environment, use synaptic to get nvidia-glx (search here for instructions, its well documented here or in the wiki). Then use the same process to switch from vesa to "nvidia"

---

### Post by Ocxic on 2006-01-26
when you get to a terminal type
```
 sudo dpkg-reconfigure xserver-xorg 
```
that will allow you to reconfigure the x windows system to you likeing and make sure everything is setup properly.
nutz u beat me to it Qrk

---

### Post by TecSoft on 2006-01-26
Thank you I am going to try it now.

---

### Post by TecSoft on 2006-01-27
Okay it worked. I can go into Gnome. Everything works including sound!!!!

---

