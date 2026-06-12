---
title: "Plymouth display on ATI 9200SE"
date: 2010-06-30
forum: General Help
---

### Post by ajgreeny on 2010-06-30
Since I began with Lucid on May 10 2010, I have been suffering with an annoying problem of the Plymouth display showing for a second or two, then changing to a resolution that puts the display on the right hand side of the screen with only the letters UBU of ubuntu showing on the far right, and with a strange pale brown/purple granular background.  I have searched these forums for an answer with no luck at all from any of the solutions offered, mainly for nvidia cards, I accept, but I'll try anything as long as it's reversible.

Quite by accident I came across an old xorg.conf file from somewhere in my own backups folder, and thought it worth a try, which I am prepared to do with any candidates I can find.  I have 11 variations that I have tried over these few weeks, none of which made any difference until this old one.  Here's the working part of the file, just in case others may find it also helps them.

It allows compiz to run without too many problems, though the rendering refresh rates are still not up to where they were in all the Ubuntu versions prior to  10.04, and I still find that 16 bit colour gives a better, less jerky display, as it did in 9.10.

xorg.conf
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen        0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
EndSection

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
    Option        "AGPMode"        "8"
    Identifier    "Card0"
    Driver        "radeon"
    VendorName    "ATI Technologies Inc"
    BoardName     "RV280 AP [Radeon 9200 PRO]"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    Option     "Accel"    "True"
    SubSection "Display"
    Viewport   0 0
    Depth     16
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

```Any comments welcome on the reason for plymouth display now working with this xorg.conf will certainly help me understand more how this all fits together.


EDIT:

I think you can dismiss a lot of what I have said here.  Further investigation and a bit of time running with this xorg.conf has shown a few things that did not come to light immediately.

1.  The system was actually still running 24 bit colour as the colour depth was showing incorrectly in the Display subsection, and should have read **DefaultDepth  16**.  Sorry about that.

2.  The ability to show plymouth correctly is apparently related to colour depth, as having changed to real 16 bit colour from what was actually 24 bit I now have the plymouth problem back again.  Very annoying!
16 bit is still unfortunately giving better all-round performance.

3.  After running for any length of time the screen rendering refresh was not as good as I had at first noted and soon dropped from around 3000 frames per 5 secs in glxgears to around 1400.  This is the most upsetting part as up to karmic I had around 8000 - 9000.  Now 3000 is my top frame rate with any xorg.conf, or indeed with no such file.

Sorry for any inconvenience caused to anyone who may have tried this version of xorg.conf.

---

