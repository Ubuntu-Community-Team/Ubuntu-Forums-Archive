---
title: "Lost sound on ubuntu 9.10"
date: 2010-02-14
forum: General Help
---

### Post by slobodan on 2010-02-14
My laptop Amilo 2540 lost sound completely.
I've installed fresh yesterday, wiped out  whole disck and there is no other installation. First everything was ok then after I switched on the ATI graphic drivers sound get lost.

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by flippo on 2010-02-14
did you check:
```
alsamixer
```
and make sure your not muted on a channel you need?

---

### Post by slobodan on 2010-02-14
Looks Ok
[http://img709.imageshack.us/i/screenshotpa.png/](http://img709.imageshack.us/i/screenshotpa.png/)

---

### Post by slobodan on 2010-02-14
It seems that Software modem driver was making a problem. Thanks to author of [http://ubuntuforums.org/showthread.php?t=1329955](http://ubuntuforums.org/showthread.php?t=1329955) Gillimaster

---

