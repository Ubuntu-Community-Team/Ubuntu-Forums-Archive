---
title: "UDEV rule for Garmin device does not work"
date: 2010-07-17
forum: General Help
---

### Post by foobar66 on 2010-07-17
Hi

I added the following rules to UDEV for my Garmin GPS device:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="091e", ATTR{idProduct}=="0003", MODE="666", RUN+="/sbin/modprobe garmin_gps", ENV{GENERATED}="1"

ACTION=="remove", SUBSYSTEM=="usb", ATTR{idVendor}=="091e", ATTR{idProduct}=="0003", RUN+="/sbin/rmmod -w garmin_gps", ENV{GENERATED}="1"

Upon inserting the device, the module garmin_gps is loaded => this works (first rule), I can see the module with lsmod

Upon removing the device, the second rule is not working. It should remove the module garmin_gps but when I do lsmod then it is still predent.

Any clue?

---

