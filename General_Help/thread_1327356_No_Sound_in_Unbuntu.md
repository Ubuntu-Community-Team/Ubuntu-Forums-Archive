---
title: "No Sound in Unbuntu"
date: 2009-11-15
forum: General Help
---

### Post by skyblueheel on 2009-11-15
A recent update resulted in having no sound.

I have tweaked Preferences / Sound preferences without success.

---

### Post by Zoot7 on 2009-11-15
What version of Ubuntu are you using? Karmic? Jaunty?

Also, can you post the output of this?
```
aplay -l
```

---

### Post by skyblueheel on 2009-11-16
Hi - Thanks for your assisitance

Ubuntu version 9.04    - the Jaunty Jackalope

Output from aplay -1



melissa@bantodesktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
melissa@bantodesktop:~$

---

### Post by Zoot7 on 2009-11-17
Okay Alsa sees your sound card fine.

Try installing the gnome alsa mixer, and maxing all the channels. It might just be a case of a muted channel.
```
sudo apt-get install gnome-alsamixer
```

---

### Post by P4man on 2009-11-17
Ive seen updates often mute the PCM channel for some obscure reason. The above suggestion should help resolve that, or just open 
```
alsamixer
```
from a terminal and increase the volume using the arrow keys.

---

