---
title: "no surround sound (ALC662)"
date: 2010-07-26
forum: General Help
---

### Post by xjgnsdof on 2010-07-26
Running Ubuntu 10.04 (32-bit) on a Zotac IONITX-A-U mobo. No surround sound, only stereo. There was an easy fix for this in 9.10, which doesn't work anymore because the volume control app has changed. Ideas?

---

### Post by lidex on 2010-07-26
> **elgilicious said:**
> Running Ubuntu 10.04 (32-bit) on a Zotac IONITX-A-U mobo. No surround sound, only stereo. There was an easy fix for this in 9.10, which doesn't work anymore because the volume control app has changed. Ideas?

Try using pulse audio volume control:
```
sudo apt-get install pavucontrol
```
What do you get for this
```
aplay -l
```
What profile have you selected in Sound Preferences on the hardware tab?

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)
[http://ubuntuforums.org/showthread.php?t=1491347](http://ubuntuforums.org/showthread.php?t=1491347)
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

---

### Post by xjgnsdof on 2010-07-26
No dice. Pulse Audio Volume Control only shows L and R speaker sliders. 

Sound profile is "analog duplex," as there is no surround sound option in the dropdown menus.

I will try the asoundrc suggestion in one of the links, though I think I've tried something like that already.

Output from aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2010-07-26
Pavucontrol will show the individual channels as will preferences once you configure asound and select the correct profile.

---

### Post by xjgnsdof on 2010-07-27
I set ALC662 as the sound card in the asoundrc file, but the speaker test couldn't recognize it, so I got no sound.

---

