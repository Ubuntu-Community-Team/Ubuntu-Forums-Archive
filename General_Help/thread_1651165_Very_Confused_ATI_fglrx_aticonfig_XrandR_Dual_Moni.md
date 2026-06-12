---
title: "Very Confused: ATI fglrx aticonfig XrandR Dual Monitors, Big Desktop"
date: 2010-12-22
forum: General Help
---

### Post by raucous1 on 2010-12-22
So I stupidly bought a new computer with an ATI RADEON HD 5700.

I have been trying to get dual monitors to work, but have been stymied by xrandr. Many forums here seem to recommend disabling xrandr to get aticonfig working. 

Why?

Is there a way for xrandr to work with dual monitors and ATI? Should I just disable it so I can use aticonfig (and xorg.conf I think). 

I am just trying to get clarification on what I should be doing.

---

### Post by raucous1 on 2010-12-22
Further details on my specific issue.

My card has a DVI and HDMI output. I have an HDTV and flatpanel monitor. If I connect the DVI to my monitor, and the hdmi to the TV, ubuntu will only allow me to set the TV as the default desktop.

If I connect it the other way (HDMI to the monitor, VGA to the HDTV) the monitor displays the desktop inside black borders (it basically is "letterboxed" on all sides).

I just want to fix this issue, but I have been very confused by the ati driver, aticonfig, and xrandr.

---

### Post by raucous1 on 2010-12-23
So I have tried every iteration of 

> xrandr --output CRT2 --auto --left-of DFP2

xrandr --output DFP2 --auto --right-of CRT2

but nothing seems to allow my HDTV (DFP2) to be the secondary dispay when its connected by HDMI. I am always forced to either clone, or use CRT2 as the secondary desktop. DFP2 will not accept being the secondary, not matter what command I give it. So basically, I am forced to use my TV as the primary desktop, which makes no sense.

Also, if I hot plug the HDMI cable in from DFP2, I just loose display immediately on my CRT2 (dvi->vga) and it switches to the DF2 as the sole primary.

It seems xrandr (or my hardware/driver?) has failed me here.

---

