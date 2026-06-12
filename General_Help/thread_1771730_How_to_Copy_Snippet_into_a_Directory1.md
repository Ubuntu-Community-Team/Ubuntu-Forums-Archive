---
title: "How to Copy Snippet into a Directory1"
date: 2011-05-30
forum: General Help
---

### Post by Metungkp on 2011-05-30
I need to save this touchscreen configuration into a directory, so that I don't have to reconfigure each time I use my touchscreen.

I need to copy this snippet below to - /usr/share/X11/xorg.conf.d/

[B]Section "InputClass"
 Identifier	"calibration"
 MatchProduct	"Fujitsu Component USB Touch Panel"
 Option	"Calibration"	"128 3826 264 3960"
EndSection[/B]

/usr/share/X11/xorg.conf.d/


[https://bugs.launchpad.net/ubuntu/+source/xinput-calibrator/+bug/776946](https://bugs.launchpad.net/ubuntu/+source/xinput-calibrator/+bug/776946)

---

