---
title: "USB Soundcard not detected aplay -l"
date: 2010-09-14
forum: General Help
---

### Post by Vigh on 2010-09-14
Hi I recently un-installed pulse-audio via the command

sudo apt-get remove --purgeall pulse-audio

to try and fix a problem with the sound-system crashing during skype calls.

I have since solved this problem by disabling a gstreamer package which was suggested to me after reinstalling pulseaudio. Unfortunately my USB-soundcard is not detected now, it is a novation xio and is supported by ALSA and is class compliant.

How can I get the usb-soundcard detected in aplay -l again. Thanks.

---

### Post by Vigh on 2010-09-14
It appears the lsusb the device is listed but there are 2 device 5s, the webcam and the usb soundcard. Could they be conflicting? And if so how do i resolve this issue.

Bus 002 Device 005: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 1235:0007 Novation EMS 
Bus 006 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1241:1603 Belkin 
Bus 001 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by kelcey_s on 2010-09-15
I am having the same problem. I hope someone can help.

---

### Post by ahnise on 2010-09-26
I have this problem also. though I had upgraded the alsa version. At first I had USB and no internal card, now I have internal card but no USB. In both cases dead card did not appear on aplay -l but appeared elsewhere

---

### Post by Vigh on 2010-09-28
goodnews is pulseaudio now works on the latest development release. they fixed gstreamer i believe. skype is working perfectly and so is my usb soundcard. going to be a really polished professional release.

---

