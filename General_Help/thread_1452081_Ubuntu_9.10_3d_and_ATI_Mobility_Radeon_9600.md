---
title: "Ubuntu 9.10: 3d and ATI Mobility Radeon 9600"
date: 2010-04-11
forum: General Help
---

### Post by alemito on 2010-04-11
Hi all,

I've issues to enable 3D effects by Compiz on Ubuntu 9.10 using a laptop with ATI Mobility Radeon 9600 video card. Infact, setting the effects in the desktop I get "Impossible to enable graphical effects".

Here some details, I'm also sure to use correct drivers, i.e. Radeon one provided by Ubuntu (no proprietary driver hardware).

#COMPIZ-CHECK
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

#XORG.CONGSection "Device"
   Identifier   "Default Device"
   Driver         "radeon"
EndSection

I' ve read a lot but no way ... please could you help ?


Thanks and best regards,
Ale

---

