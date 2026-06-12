---
title: "Saving Into a Directory"
date: 2011-05-30
forum: General Help
---

### Post by Metungkp on 2011-05-30
According to this link (below) I need to copy my touchscreen configurations, so that I don't have to reconfigure each time I want to use my touchscreen.
[https://bugs.launchpad.net/ubuntu/+source/xinput-calibrator/+bug/776946](https://bugs.launchpad.net/ubuntu/+source/xinput-calibrator/+bug/776946)

The directory is - **/usr/share/X11/xorg.conf.d/**

I need to copy this snippet (below) in to this directory:

[B]Section "InputClass"
 Identifier	"calibration"
 MatchProduct	"Fujitsu Component USB Touch Panel"
 Option	"Calibration"	"128 3826 264 3960"
EndSection[/B]

I found the directory but its read only and I'm unsure as to how to do it in Terminal.

Thanks!
KP

---

### Post by Metungkp on 2011-05-30
I found the answer> gksudo gedit

---

