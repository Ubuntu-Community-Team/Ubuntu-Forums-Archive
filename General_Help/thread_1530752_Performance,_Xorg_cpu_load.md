---
title: "Performance, Xorg cpu load"
date: 2010-07-14
forum: General Help
---

### Post by pavelagp on 2010-07-14
Hello.
**1.** Using top command i found that Xorg process load my CPU up to 30% when idle and 90% if i just move any window across desktop.
I  solved this problem:D
I replace libgl1-mesa-swx11 package with libgl1-mesa-glx.
And add Option "VideoOverlay" "true" to Device section.
Now Xorg not load CPU while idle and load 8-10% while video played or opengl application runs. 

**2.** I compare Xubuntu 10.04 and PC-BSD 8.0 for opengl preformance.
I use IBM T40 (PM 1.6ghz/1024 RAM/80HDD/Radeon Mobile 7500) for this test and glxgears.
xorg.conf was same.
And i have next results:
Xubuntu 10.04 - 2400 frames
PC-BSD 8.0 - 5600 frames
I dont understand why PC-BSD  twice fast ?

**My xorg.conf**
> Section "Module"
        
        Load    "drm"
        Load    "glx"
        Load    "dri"
    Load    "dri2"
    Load    "v4l"
EndSection

Section "Device"
    Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
    Boardname    "ATI Radeon"
    Driver        "radeon"
    Vendorname    "ATI"
    Option          "AccelMethod" "XAA"
    Option          "AGPFastWrite" "true"
    Option        "AGPMode" "4"
    Option        "AllowGLXWithComposite" "true"
    Option        "Colortiling" "On"
    Option        "DRI" "true"
    Option        "EnablePageFlip" "True"
    Option        "FBTexPercent" "50"
    Option        "GARTSize"    "256"
    Option        "MergedFB"    "off"
    Option        "MigrationHeuristic" "greedy"
    Option        "RenderAccel" "true"
    Option        "UseInternalAGPGART" "yes"
    Option        "XAANoOffscreenPixmaps"
    Option "VideoOverlay" "true"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Radeon Mobility 7500"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1024x768@60" "800x600@60" "640x480@60"
  EndSubSection
EndSection

Section "Extensions"
    Option  "Composite" "Enable"
EndSection

 Section "DRI"
   Mode 0666
 EndSection

---

