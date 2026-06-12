---
title: "eGalax Promblems"
date: 2010-06-01
forum: General Help
---

### Post by xtjacob on 2010-06-01
Hi, I'm running ubuntu 10.04 64-bit on a Dell XFR D630 and whenever I touch the screen the pointer always goes to the upper left hand corner. I've tried using xinput_calibrator_x11 to calibrate it, but it only sees me touching the first cross hair and none of the other ones. Also when I run ```
sudo xinput set-prop --type=int --format=8 "eGalax Inc. USB  TouchController" "Evdev Axes Swap" 1
``` It says "unable to find device eGalax Inc. USB  TouchController". How can I get this to work?

---

