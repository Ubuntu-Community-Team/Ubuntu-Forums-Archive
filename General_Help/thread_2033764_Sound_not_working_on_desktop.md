---
title: "Sound not working on desktop"
date: 2012-07-26
forum: General Help
---

### Post by epikvision on 2012-07-26
I own a Realtek ALC892 sound card for my desktop sound, and I don't seem to be getting any sound out of it since this afternoon.  

Before the sound went out, i used synaptic manager to get the nvidia-current package, seeing how slow the card animations in quizlet.com went.  After an install, I have no more sound.

I need help restoring the sound back to my speakers.

---

### Post by sorooshubu on 2012-07-26
Please send output of these commands:
aplay -l
 lspci | grep Audio

---

### Post by epikvision on 2012-07-26
aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci | grep Audio
> 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
01:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)


---

### Post by sorooshubu on 2012-07-26
I guess if you reinstall alsa and some sound related package this problem will be solved
use this command
```

sudo apt-get --reinstall install linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

```If problem exist, following link may be useful.
[https://help.ubuntu.com/community/SoundTroubleshooting/](https://help.ubuntu.com/community/SoundTroubleshooting/)

---

