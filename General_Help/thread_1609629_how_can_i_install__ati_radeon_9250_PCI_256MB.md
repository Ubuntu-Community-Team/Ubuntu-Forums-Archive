---
title: "how can i install:  ati radeon 9250 PCI 256MB"
date: 2010-10-30
forum: General Help
---

### Post by osmorphyus on 2010-10-30
as the name says it all, how can i install my ATI radeon 9250 pci video card in ubuntu?  i'd like to be able to use this with high screen res and compiz-fusion in place of my crappy  on board video gpu.



hope someone can help!

---

### Post by clhsharky on 2010-10-30
osmorphyus

ATI radeon 9250 chips is very old technology and you can only use the open drivers that are installed by default.
The OS will recognize and lode drivers on first start up.
If it is true this card is pci, it is installed in pci slot on motherboard.
PCI slots share IRQs with other components so you may have to try different slots to avoid conflicts to get a working system. 
Also pci slots have a narrow bandwidth so don't expect high performance compared to AGP ports of that era.

Sharky

---

### Post by osmorphyus on 2010-10-30
this is all fine, but how can i get higher screen resolution?  this is kinda gay being stuck at 1024x768.

im using the radeon card now, hope someone can help!

---

### Post by osmorphyus on 2010-10-31
bump:  still need higher resolution, guys.  thanks.

---

### Post by osmorphyus on 2010-11-01
bump

---

### Post by osmorphyus on 2010-11-01
bamp

---

### Post by mastablasta on 2010-11-01
don't bump the thread unless it's more than 2 days old.

have you tried changing the resolution?

---

### Post by osmorphyus on 2010-11-01
yeah, of course i tried, and it cuts off at 1024x768.

so how can i get the full potential here?

---

### Post by osmorphyus on 2010-11-02
any info on getting higher resolution out of my radeon card?  i cant push it beyond 1024x768 at the moment.  also, visual effects are not available.

is there any driver tweaking i can do?

---

### Post by osmorphyus on 2010-11-02
i have an ati radeon 9250 pci card, i cant get a higher resolution beyond 1024x768.

i tried changing the resolution but its maxed here.  this card is capable of much higher resolutions in wnidows environments.


what do i have to tweak to get a full range of possible resolution scales?  i also suspect i do not have openGL support since openGL screensavers and most games will not load for me.



i get no screen effects either.

---

### Post by ajgreeny on 2010-11-02
See what the output of *glxinfo* in terminal tells you. It should say **direct rendering: yes** a few lines from the top.

You may find that to get better resolution you need to customise your /etc/X11/xorg.conf file, which is probably non-existent at the moment on your machine.

Here's the working part of mine needed for 10.04 lucid, with a 9200SE card which used to work great until karmic, 9.10, when it was a pain in the neck.  Now with maverick it is great again, even without an xorg.conf file.

```
Section "Device"
    Option        "EnableDepthMoves"    "True"
    Option        "EnablePageFlip"    "True"
    Option        "DMAForXv"        "True"
    Option        "AccelDFS"        "True"
    Option        "ColorTiling"        "True"
    Option        "RenderAccel"        "True"
    Option        "VGAAccess"        "True"
    Option        "AccelMethod"        "EXA"
    Option        "DRI"            "True"
    Option        "MigrationHeuristics"    "greedy"
    Option        "TripleBuffer"        "True"
    Option        "EXAOptimizeMigration"  "true"
    Option        "EXANoComposite"    "No"
    Option        "BackingStore"        "true"
    Option        "AGPMode"        "8"  #you may need to remove this AGPMode entry if your card is not AGP, or has a different multiplication rate.
    Identifier    "Card0"
    Driver        "radeon"
    VendorName    "ATI Technologies Inc"
    BoardName     "RV280 AP [Radeon 9200 PRO]"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "RENDER" "Enable"
    Option "Composite" "True"
    Option "XVideo" "Enable"
    Option "XINERAMA" "False"
EndSection

Section "DRI"
    Mode        0666
EndSection


```
I hope that may be of some help, but make sure you change the file contents to suit your card, monitor resolution, and all other hardware of yours compared with mine.

---

### Post by osmorphyus on 2010-11-02
thank you for the help.

alright, when i open terminal and run glxinfo, it returns with:

name of display:  0.0
segmentation fault


where do i go from here?  as well, how do i find if i have/need a xorg file?

---

### Post by osmorphyus on 2010-11-03
im goin to work, ill check back in 8 hours.  

thanks to anyone hwo reads this and can help.

---

### Post by osmorphyus on 2010-11-05
bump

---

### Post by osmorphyus on 2010-11-05
oh my god, can i get some help with this or what the hell?

---

### Post by osmorphyus on 2010-11-06
For the love of bacon im starting a new thread for this.  Bump.

---

