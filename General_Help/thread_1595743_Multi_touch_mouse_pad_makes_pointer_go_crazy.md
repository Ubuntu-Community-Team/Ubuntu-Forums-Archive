---
title: "Multi touch mouse pad makes pointer go crazy"
date: 2010-10-13
forum: General Help
---

### Post by Papex on 2010-10-13
After installing 10.10 on my ACER Aspire 5739G with multi touch pad the pointer acts very very funny when I use the multi touch pad.

In most cases I can use one finger to direct the pointer and it works almost normally. But as soon as I put a second finger on the pad the pointer goes nuts on the screen.

Even sometimes it activates links even though I'm just using one finger. 

In any case: I believe this issue could be fixed pretty easily but I don't know how. I guess I need a special driver or piece of software to get this under control.  

Can anybody help me out here?

BTW: Normal USB mouse works fine.

Thank you!

---

### Post by Papex on 2010-10-14
anyone??

---

### Post by Sub101 on 2010-10-14
You need to set the multitouch features.

The script below does that:

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
sleep 20 #added delay...
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 9         #  Below width 1 finger touch, above width simulate 2 fing$
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 1 1 0       #  vertical, horizontal, corner - values: 0=disable  1=ena$
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 #  stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 1 2 3   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulat$
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   #  vertical scrolling, horizontal scrolling - values: 0=di$
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling" 1
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling Trigger" 3

exit


```

---

### Post by digitalWestie on 2010-12-22
hey- did this work? All of a sudden I have the same problem!

---

