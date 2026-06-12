---
title: "HDMI help Ubuntu 10.10"
date: 2010-11-11
forum: General Help
---

### Post by netzero on 2010-11-11
Hi I am having problems with my HDMI to my Sony TV.  The Video works  flawlessly, but the audio doesn't.  I had it installed inside Windows to  test it out and it worked, i liked it so i dual booted.  Now it doesn't  work.  In the terminal i ran ```
aplay -l
``` and i got this
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```the trouble shooting site shows,

```
*** List of PLAYBACK Hardware Devices **** 
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1 Subdevice #0: 
  subdevice #
0card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1 Subdevice #0:   
  subdevice #
0card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI] 
  Subdevices: 0/1 
  Subdevice #0: subdevice #0 

```Any  ideas? Mine doesn't show HDMI...  I really want to use Ubuntu, but I really need the sound.  I'm  not very experienced with any commands or the terminal, im pretty new  with linux.  Thanks for any help!

---

### Post by dino99 on 2010-11-11
thread like yours:

[http://ubuntuforums.org/showthread.php?t=967023](http://ubuntuforums.org/showthread.php?t=967023)

---

