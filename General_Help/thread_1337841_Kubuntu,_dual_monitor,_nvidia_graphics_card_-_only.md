---
title: "Kubuntu, dual monitor, nvidia graphics card - only one monitor active"
date: 2009-11-25
forum: General Help
---

### Post by fperloff on 2009-11-25
I just completed a brand new installation of Kubuntu 9.10, 64 bit. I have an nVidia graphics card (GeForce 9600 GT), with dual DVI outputs, and a pair of LCD monitors attached. 

When I booted from the install CD, I selected "Safe Graphics Mode" (F4); otherwise the screen would have remained black. The installation was successful. However, Kubuntu now only recognizes one monitor. That is to say, the output of xrandr only mentions one screen, and the KDE display and multiple monitor utilities only recognize one monitor:

user@ubuntu:~$ xrandr
Screen 0: minimum 640 x 480, current 1920 x 1200, maximum 1920 x 1200
default connected 1920x1200+0+0 0mm x 0mm
   1920x1200       0.0*
   1600x1200       0.0
   1280x1024       0.0
   1024x768        0.0
   800x600         0.0
   640x480         0.0

Based on /var/log/Xorg.0.log, I believe that X is using a "plain vanilla" VESA driver, instead of a driver more appropriate to an nVidia card. 

BTW, I know that the hardware is working properly, since I just booted into Windows 7, and both monitors worked properly.

How do I get X to recognize the nVidia card and give me two monitors? I realize that I could install the proprietary nVidia drivers. Is that the preferred solution among forum members? I read that in the latest release of Fedora, a patch to the X server broke nVidia's drivers in KDE, so I'm a bit reluctant.

Thank you.

---

### Post by Sin@Sin-Sacrifice on 2009-11-25
1. Safe graphics mode. That's not going to use your nvidia drivers.
2. Do you have the nvidia drivers installed?
3. If you get a black screen if using anything other then safe graphics mode then there's a problem with the xorg.conf. I would try running ```
sudo dpkg-reconfigure --phigh xserver.xorg
``` from a failsafe prompt then try to boot into your regular kernel, installing nvidia drivers, and then setting up dual monitors with the nvidia-settings.

---

### Post by audiomick on 2009-11-25
> **fperloff said:**
> ... a driver more appropriate to an nVidia card...that I could install the proprietary nVidia drivers. Is that the preferred solution among forum members? 

You don't need the nVidia ones if you're happy with the way things are working without...

Have you read this?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I am pretty sure that is the same card I am using. I have got two monitors running, but, if I remember right, it didn't work until I got the nVidia drivers. I am using Gnome. If you are concerned about KDE, install gnome as well and boot into that to try things out.

---

### Post by fperloff on 2009-11-26
SOLVED. I installed the proprietary nvidia drivers, changed the entry for "Driver" in xorg.conf from "Vesa" to "nvidia" and ran nvidia-settings.

By the way, I believe the syntax of the command referred to above should be:

sudo dpkg-reconfigure --p high xserver-xorg

Thanks for your help.

---

