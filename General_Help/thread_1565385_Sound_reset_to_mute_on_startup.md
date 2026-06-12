---
title: "Sound reset to mute on startup"
date: 2010-08-31
forum: General Help
---

### Post by mynot on 2010-08-31
Whenever I reboot my sound is muted.
Ubuntu 10.4.1

aplay -l gives:
 card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The following don't fix problem:
 1. sudo alsactl store with sound unmuted
 2. aslamixer - master is -46db; reset to 0db doesn't give me sound
 3. append "options snd-hda-intel model=auto" to "/etc/modprobe.d/alsa-base.conf"

The only thing I can find which looks sus is:
 hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
from 
 dmesg | grep hda 
(and I don't know that it is sus).

Thanks
Tony

---

### Post by mynot on 2010-12-16
This did it for me:
[https://bugs.launchpad.net/ubuntu/+s...32/comments/77](https://bugs.launchpad.net/ubuntu/+s...32/comments/77)

---

