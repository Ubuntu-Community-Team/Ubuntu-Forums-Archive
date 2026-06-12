---
title: "AR1600-U910H sound works with mythtv only (hdmi)"
date: 2009-12-31
forum: General Help
---

### Post by iitywygms on 2009-12-31
Just got a Acer Aspire Revo ar1600.  Installed mythbuntu on it and the sound works in mythbuntu only.  This is over hdmi
Sound does not work anywhere else?  Firefox, boxee or anything.
here is aplay -l.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Can anyone help?
Thanks

---

### Post by iitywygms on 2009-12-31
Fixed it.
Had to add 
defaults.pcm.device 3
to .asoundrc in my home directory.

Why mythtv works without this I dont know.

---

