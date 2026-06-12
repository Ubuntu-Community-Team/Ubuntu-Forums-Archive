---
title: "sound comes out of both speakers and headphones"
date: 2012-10-08
forum: General Help
---

### Post by MattWatts on 2012-10-08
Hello all, I am a linux newb and I am having a bit of trouble. I am running 10.04 LTS. Sound is coming out of both speakers and headphones at the same time. It doesn't appear that there is anything I can do in preferences to change this. I have looked through a few threads about this already but could not find a fix. This is a new install on my toshiba satellite. Thankyou for all advice.

---

### Post by pqwoerituytrueiwoq on 2012-10-08
are you saying your headphones work in both audio input and output or your microphone is acting like a speaker
eigher way post output of these 3 comamnds
```
lspci | grep Audio
arecord -l
aplay -l
```

---

### Post by MattWatts on 2012-10-08
> **pqwoerituytrueiwoq said:**
> are you saying your headphones work in both audio input and output or your microphone is acting like a speaker
eigher way post output of these 3 comamnds
```
lspci | grep Audio
arecord -l
aplay -l
```


The sound plays out of the headphones and the internal speakers at the same time when it should stop playing from the speakers once the headphones are plugged in.

____________________________________________
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
_______________________________________________

Thankyou for the help

---

### Post by MattWatts on 2012-10-09
Bump

---

