---
title: "Blurry display upon new install 12.04"
date: 2012-07-16
forum: General Help
---

### Post by lsutiger on 2012-07-16
I did a new install of 12.04. When the computer boots, it tries a resolution of 1920X1080, though the resolution for the monitor is 1680X1050, 60Hz. 
When I switch to the correct resolution and Hz, the screen is blurry. I had the same problem with a previous install (9.10) and all I did was reset the resolution and the display was very crisp.

Here are the hardware specs:

Monitor: SceptreX22WG-1080P
Resolution: 1680X1050 60 Hz
Viewing Angle 170°(H) / 160°(V)
Video Card: nVidia Corporation G96 [GeForce 9400 GT] 

I am controlling the resolution from the nVidia X Server Settings program. Within that program, it is reporting a refresh rate of 59.95Hz

Any idea what may be wrong here?

---

### Post by lsutiger on 2012-07-16
An answer for those who may have same problem in future:
After setting the correct resolution, I went to the DFP setting (This one has the Brand name of the monitor). Under 'Flat Panel Scaling' I unchecked 'Force Full GPU Scaling' and selected 'Centered'.

---

