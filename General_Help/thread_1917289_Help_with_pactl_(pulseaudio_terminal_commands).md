---
title: "Help with pactl (pulseaudio terminal commands)"
date: 2012-01-29
forum: General Help
---

### Post by jmadero on 2012-01-29
Hi All,

I have been trying to write a script for a long time to change pulseaudio through terminal and accidentally stumbled on pactl today but need some help. Here is my aplay

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


What I want is the command to switch to HDMI through terminal given my card listed above. Appreciate any help, the man for pactl could be a bit better, no examples listed as far as I can see

---

### Post by zibletop on 2012-03-13
Have you look at [this documentation page]("http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User") ?

---

