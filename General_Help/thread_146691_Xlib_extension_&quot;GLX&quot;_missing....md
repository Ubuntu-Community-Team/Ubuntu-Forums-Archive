---
title: "Xlib: extension &quot;GLX&quot; missing...?"
date: 2006-03-18
forum: General Help
---

### Post by fishmorg909 on 2006-03-18
Hi! Got Ubuntu nicely set up on an ol' Dell Optiplex GX1. The rendering for glxgears was very slow (and could not run TuxRacer). Then I used Synaptic to install nvidia-glx-legacy, and now glxgears will not run. I get error message

Xlib: extension "GLX" missing on display ":0.0".
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

Everything's running fine otherwise, but is there a way to turn on double-buffering, and get my setup to find GLX? I've been looking all over.

---

### Post by jpkotta on 2006-03-18
Why did you install nvidia-glx-legacy when you have an ATI card?  Install ATI drivers if you have an ATI card.  Instructions are in the wiki.

---

### Post by fishmorg909 on 2006-03-18
Well, I went to the wiki page [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
... and followed the instructions to install "Ubuntu provided drivers." At one point it said:

**"If ati is auto-selected at the video card selection screen, then go down to select fglrx. Leave other settings to their default value**."

THAT WAS NO GOOD. My system got hung at bootup and I had to run 
sudo dpkg-reconfigure xserver-xorg in order to change it back to ATI. Then it booted normally. I can get glxgears again, but verrry slow. In terminal the error message shows:

> Xlib:  extension "XFree86-DRI" missing on display ":0.0"

(Which is why I tried installing nvidia-glx-legacy, but I uninstalled it before doing all the above.)

So... any advice on the XFree86-DRI error?

---

