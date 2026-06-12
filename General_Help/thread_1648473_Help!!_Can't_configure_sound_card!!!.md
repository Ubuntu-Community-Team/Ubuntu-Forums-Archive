---
title: "Help!! Can't configure sound card!!!"
date: 2010-12-18
forum: General Help
---

### Post by arashiko28 on 2010-12-18
Actually I had solved this problem back to 8.10, but now on maverick, none of the tricks have worked. Either I have a low sound and the speakers keeps going on with the headphone plugged in, or there is no sound at all. On this thread:

> [http://ubuntuforums.org/showthread.php?t=995940](http://ubuntuforums.org/showthread.php?t=995940)

I had it solved, but now, none of this configurations seems to work, and something has changed as you can see, this was my old aplay -l list:

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0

and this is my new aplay -l list:
> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[B]card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


The one in bold actually didn't existed before and I can't find a way to configure it, the laptop specs are on my signature, please, help :cry::-({|=

---

### Post by arashiko28 on 2010-12-18
Truth to be told, this hurts, the fact is I had to go back 2 kernel versions, in order to get my sound back to work. Had to reinstall 2.6.34.

---

