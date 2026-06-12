---
title: "Sound problem"
date: 2010-12-29
forum: General Help
---

### Post by d_darlac on 2010-12-29
Just made a clean install (10.10) on a new AUS N53J - all works fine, except sound - cannot get any sound from speakers - I noticed many problems with the sound on this version of Ubuntu, and I tried all posted suggestions - still no sound...
any help will be greatly appreciated

---

### Post by d_darlac on 2010-12-29
Does this look right? 
still no sound....
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by d_darlac on 2010-12-30
fixed it with some googling - 
just added:
options snd-hda-intel model=auto position_fix=0

at the end of /etc/modprobe.d/asa-base.conf

depending on your pc this needs to be adjusted...

---

