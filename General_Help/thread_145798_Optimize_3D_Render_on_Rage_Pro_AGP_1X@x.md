---
title: "Optimize 3D Render on Rage Pro AGP 1X/@x?"
date: 2006-03-17
forum: General Help
---

### Post by fishmorg909 on 2006-03-17
Hi! Got Ubuntu nicely set up on an ol' Dell Optiplex GX1. The rendering for glxgears was very slow (and could not run TuxRacer). Then I used Synaptic to install nvidia-glx-legacy, and now glxgears will not run. I get error message

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Here's the ATI setup:

VGA compatible controller
product: 3D Rage Pro AGP 1X/2X
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@01:00.0
version: 5c
size: 16MB
width: 32 bits
clock: 33MHz
capabilities: vga bus_master cap_list

Everything's running fine, but is there a way to optimize 3D rendering here? Thanks.

---

### Post by Trackieman on 2007-02-24
I'm puzzled as to why you installed nvidia-glx-legacy when you are using an ATI card?
You should use xserver-xorg-video-ati with Driver "ati" in your /etc/X11/xorg.conf

It's going to be too old for the newer xorg-driver-fglrx I think.

---

### Post by lexscholar on 2007-03-09
Linux NooB, here.  I have the same GX1 as the OP.  This is my first attempt at Linux.  My standard 6.10 Ubuntu install went fine from the CD and the auto updates worked flawlessly (and smokin' FAST downloads!).  Everything seems to be working fine on this antique computer.  I have noticed that the graphics aren't as "crisp" as when the same machine ran Win 2K.  I'm really not sure why or if this is even a valid complaint!

But, I am a tweaker, and part of this whole Linux endeavor for me is to discover Linux' abilities and limitations (as well as mine).  My modest research indicates there are different "driver" packages like, ATI and Xorg.  I'm not even sure if they aren't already included and installed.  
[B]
My question is, are they already installed, and if not, are there any performance gains to be had if I attempt to install on of these alternative packages?[/B]  My expectations are realistic, I'm not looking for x1900 performance.

I am enclosing a screenshot from the Device Manager showing the integrated graphics, as installed.

---

### Post by Trackieman on 2007-04-10
Darn, I should check the Threads more often sorry!

Looks like your stuck with legacy ATI

---

### Post by sTpny on 2008-01-25
I've got the same computer as you. It's got gutsy gibbon on it now. I think Feisty faun actually worked a little bit better on it, as it would hibernate and suspend before I upgraded. Anyhow, I too am looking to get the 3d graphics enabled. I know the machinr is capable of it, but setting it up is another story. I'll post the solution if I find it and you do the same. ok.

---

