---
title: "no sound after upgrade to ubuntu 11.10"
date: 2012-02-13
forum: General Help
---

### Post by redsprite on 2012-02-13
hello all,
no sound after upgrade to ubuntu 11.10
 this is my output for :
 sudo aplay -l
------------
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by HiImTye on 2012-02-13
whats the output of
```
 apt-cache policy alsa-base
```
and
```
cat ~/.asoundrc
```

---

