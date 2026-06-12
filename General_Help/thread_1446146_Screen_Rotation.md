---
title: "Screen Rotation"
date: 2010-04-03
forum: General Help
---

### Post by dashpunk on 2010-04-03
Hey,
I wanted to rotate my screen 90 deg, and i do not know if its even possible
i have a lenovo t61 14.1 wxga, ubuntu 9.10
using a quadro nvs 140m graphics card

in xorg.conf details:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    Option          "RandRRotation" "on"
EndSection

when i type: xrandr -o left

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

... I was wondering if there is a way to fix this.

Thanks for your help!

---

