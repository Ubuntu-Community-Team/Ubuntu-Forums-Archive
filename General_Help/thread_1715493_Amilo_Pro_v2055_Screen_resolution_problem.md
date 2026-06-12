---
title: "Amilo Pro v2055 Screen resolution problem"
date: 2011-03-27
forum: General Help
---

### Post by elathderon on 2011-03-27
Hello!

I've just installed Ubuntu 10.10 on my laptop (AMILO Pro v2055 with Via IGP) but just can't get it work  right. The screen resolution is set to 1600x1200 but the max. resolution  on this notebook is 1280x800.
If I try to reset the resolution for any other than 1600x1200 the screen  will 'explode' and I cant even tell where the cursor is. :confused:

I've tried many things includeing editing grub.conf and xorg.conf but without any success. :(

I'd be glad for any help or idea!

---

### Post by vg2373 on 2012-07-06
Just have done it myself, so should work. Contents of xorg.conf are as follows:
-------------------------------------------------------------------------------------------------------------------------------

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "Emulate3Buttons"    "true"
EndSection


Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection
Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "vesa"
    Busid        "PCI:1:0:0"
    Driver        "openchrome"
    Screen    0
    Option "SWcursor" "true"
    Option "EnableAGPDMA"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    Horizsync    31.5-50.0
    Vertrefresh    56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "1280x800@60"    "800x600@56"
    Virtual    1280 768
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "dri"
    Load        "v4l"
EndSection
Section "device" # 
    Identifier    "device1"
    Boardname    "vesa"
    Busid        "PCI:1:0:0"
    Driver        "openchrome"
    Screen    1
EndSection
Section "screen" # 
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection
Section "monitor" # 
    Identifier    "monitor1"
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection                      
-----------------------------------------------------------------------------------------------------------------------------
Good luck.

---

### Post by overdrank on 2012-07-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

