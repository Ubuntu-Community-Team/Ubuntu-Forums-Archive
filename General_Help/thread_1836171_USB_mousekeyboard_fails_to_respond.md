---
title: "USB mouse/keyboard fails to respond"
date: 2011-08-30
forum: General Help
---

### Post by WonderStivi on 2011-08-30
Occasionally, my computer freezes up and does not respond to mouse movement or keypresses. If I press the power button, the log-off dialogue appears, and pressing the power button a second time will make the PC shutdown after 60 seconds, as normal shutdown.

I checked the syslog (I'm not really experienced at finding causes in log files) and found this line:
failed in opening HIDDEV file: /dev/usb/hiddev0. Permission denied

This line is repeated several times for several devices, and also repeatedly over a long time period.

It seems that usb-daemon or whatever seizes to respond after a random amount of time.

Anyone with a solution to this problem? I'm running Natty X64. Pfft, can't remember mouse version... Mouse is bluetooth and keyboard is Logitech K800.

---

