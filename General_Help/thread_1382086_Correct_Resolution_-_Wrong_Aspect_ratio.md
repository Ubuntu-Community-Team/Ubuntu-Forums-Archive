---
title: "Correct Resolution - Wrong Aspect ratio"
date: 2010-01-15
forum: General Help
---

### Post by AxlDLuffy on 2010-01-15
Good evening. I'm facing the following problem:

My monitor is a Samsung P2370, 23 inches. It's native resolution is 1920x1080@60Hz. My graphic card is an ATI 4890. My first challenge was to force my screen to display at 1920x1080. After a long time (maybe I should blame ATI for that :) ) I made it. Only the Odessey continues. Although the resolution right now is 1920x1080, it takes up only the center of the screen. To be more accurate, there is a gap, right and left of the screen. Imagine as you have a res of 1920x1080 (16:9) only it is strech down to 4:3. That happens only with this very resolution. If I set the monitor to display on a lower resolution, the screen takes up the 100% of the screen as expected. The menu of my monitor does not have the option of strecthing the screen, only the auto-fix button which doesn't seems to help. 
Here's the xorg.cong file (The values of HorizSync and VertRefresh are correct)

```
Section "ServerLayout"
   Identifier     "aticonfig Layout"
   Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
   Load  "glx"
EndSection

Section "Monitor"
   Identifier   "aticonfig-Monitor[0]-0"
   HorizSync    30.0 - 81.0
   VertRefresh  56.0 - 60.0
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection

Section "Monitor"
   Identifier   "aticonfig-Monitor[0]-0"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection

Section "Device"
   Identifier  "aticonfig-Device[0]-0"
   Driver      "ati"
   Option       "UseFastTLS" "1"
   BusID       "PCI:4:0:0"
EndSection

Section "Device"
   Identifier  "aticonfig-Device[0]-0"
   Driver      "fglrx"
   BusID       "PCI:4:0:0"
EndSection

Section "Screen"
   Identifier "aticonfig-Screen[0]-0"
   Device     "aticonfig-Device[0]-0"
   Monitor    "aticonfig-Monitor[0]-0"
   DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
      Depth     24
      Modes    "1920x1080" "1680x1050" "1440x900" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
   EndSubSection
EndSection
```Thank you for all your help and excuse my poor english. :)

---

