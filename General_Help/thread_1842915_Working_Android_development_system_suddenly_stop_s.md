---
title: "Working Android development system suddenly stop seeing my Samsung Galaxy Tab!"
date: 2011-09-12
forum: General Help
---

### Post by RodneyLambert on 2011-09-12
I feel like an update to Ubuntu is the root cause of the Tab not being detected by the ADB and would like suggestions of how to debug what is going on.  

Summary of the situation:
Ubuntu 10.10 - 2.6.35-30-generic
This is a working Android development system and I have been targeting the Galaxy Tab 10.1 since I got it in May.  As of last week the ADB does not see the device.  The ADB sees my other devices, HTC and LG.  On my Windows system the ADB does see the Tab so I don't think it is the Tab that is causing the problem.

When I run adb devices I get no results, I do not get the ?????? it just does not see the device.  lsusb does see the device as expected.  My gut says that something has changed about how the device is being detected via udev but I don't know what or how.

It should be noted that after spend several days researching what might have happened the device suddenly showed up again!  Today it can't be found!

---

