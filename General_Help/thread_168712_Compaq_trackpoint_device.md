---
title: "Compaq trackpoint device"
date: 2006-05-01
forum: General Help
---

### Post by Eric_T on 2006-05-01
Hello

I have a Compaq Evo N800c with a trackpoint device ala IBM Thinkpads(I think Compaq calls it a concerto pen or something like that...). The problem is that the operation is a lot smoother and faster in Windows than in Linux. Is there some way to remedy this?

---

### Post by ceoran on 2006-05-13
[QUOTE=Eric_T]Hello

I have a Compaq Evo N800c with a trackpoint device ala IBM Thinkpads(I think Compaq calls it a concerto pen or something like that...). The problem is that the operation is a lot smoother and faster in Windows than in Linux. Is there some way to remedy this?[/QUOTE]

Edit your xorg.conf (/etc/X11/xorg.conf) and find the section "InputDevice". Replace it with the following (and remember to make a backup from xorg.conf):

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SHMConfig"    "true"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge"      "1700"
Option "RightEdge"     "5300"
Option "TopEdge"       "1700"
Option "BottomEdge"    "4200"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "VertScrollDelta" "100"
Option "MinSpeed" "0.05"
Option "MaxSpeed" "0.10"
Option "AccelFactor" "0.0011"
EndSection


By the way, I'm using the same laptop :) have you got the powermanagement working? my laptop's fan goes always at full speed.

---

