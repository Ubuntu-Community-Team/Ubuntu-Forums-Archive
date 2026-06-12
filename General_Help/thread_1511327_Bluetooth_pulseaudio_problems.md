---
title: "Bluetooth pulseaudio problems"
date: 2010-06-16
forum: General Help
---

### Post by Cuppa-Chino on 2010-06-16
Hi,

I have a sony vaio e-series with bcm 2070 foxconn t77h114 bluetooth chip. I want to stream music via bluetooth to my stereo using a belkin bluetooth audio receiver.

this works okayish under windows, occaisonal gaps in playbay but all in all ok.
under linux there are times when it seems to go okay but most of the time it just cuts in and out at an amazing rate.

log files report that pulseaudio skips this and that amount of micro seconds, anybody been able to fix this kind of problem?

I am using blueman and have updated to the latest bluez packages from ppa but no real change.



thanks
```
Jun 17 08:14:49  pulseaudio[1834]: module-bluetooth-device.c: Skipping 130464 us (= 23012 bytes) in audio stream
Jun 17 08:14:50  pulseaudio[1834]: module-bluetooth-device.c: Skipping 1354756 us (= 238976 bytes) in audio stream
Jun 17 08:14:51  pulseaudio[1834]: module-bluetooth-device.c: Skipping 179786 us (= 31712 bytes) in audio stream
```
etc etc

---

