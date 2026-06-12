---
title: "Ubuntu is using VESA instead of intel"
date: 2012-08-25
forum: General Help
---

### Post by Linias on 2012-08-25
Hi,
I am using Ubuntu 12.04 (32).
I have a graphic card:
Intel corporation 82945G/GZ Integrated Graphics Controller

and monitor:
Acer,  max resolution 1920x1080

After installation of the OS I have options only from VESA (output of xrandr):
***
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

***
That is really quite bad for eyes.. everything is too much wide.

I have tried searching the web, generating xorg.conf (ending by incorect settings), adding mode by xrandr (ending by "crtc failed"), using intel drivers (ppa:glasen/intel-driver), installing another linux distributions (openSuse, Mint, debian) - all the same... so probably this is not issue of Ubuntu, but the linux kernel and intel itself.
On Microsoft Windows its without problem.

Does somebody have some ideas how to fix it?
I am not a linux guru, so please if you have some advices, tell me how to do it :)

Thank you.

---

