---
title: "Recognize joysticks and put them in the same order each time"
date: 2009-12-01
forum: General Help
---

### Post by stobi on 2009-12-01
Hi All,

I am trying to set up a flight simulator (based on X-Plane), and am heavily struggling to get three joystick-devices (joystick, ruder pedals and throttle quadrant) working correctly.

Basically I encounter two problems:
1. One device (the pedals) is not recognized at boot. What I figured out so far, that it is maybe answering two slowly and therefore not recognized by the system. I have to unplug and replug it in order to be recognized, hence functional.

2. The other devices are assigned to /dev/input/js0 and js1 randomly. Like this, my preferences in X-Plane do not work at all, because it expects the devices to always be in the same order, and it happens that the throttle controls my flight controls and vice versa.

I tried several approaches published here in the forums (restart udev, write a udev rule, try to restart the usb,...) without success.

Any help would be appreciated!

Stefan

---

