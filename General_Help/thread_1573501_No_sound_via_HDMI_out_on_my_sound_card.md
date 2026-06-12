---
title: "No sound via HDMI out on my sound card?"
date: 2010-09-12
forum: General Help
---

### Post by bilekbp on 2010-09-12
Hello, I recently installed an NVidia GeForce 240 in my HTPC, and finally got it working correctly (as an HDMI-out display) in Lucid Lynx 64-bit.

My problem now is that there is no sound, even though sound should be passing through, and I don't know where to begin to fix the issue.

Does anyone have any ideas?

Thanks!

---

### Post by dcstar on 2010-09-13
> **bilekbp said:**
> Hello, I recently installed an NVidia GeForce 240 in my HTPC, and finally got it working correctly (as an HDMI-out display) in Lucid Lynx 64-bit.

My problem now is that there is no sound, even though sound should be passing through, and I don't know where to begin to fix the issue.

Does anyone have any ideas?

Thanks!

System-Preferences-Sound

---

### Post by bilekbp on 2010-09-13
> **dcstar said:**
> System-Preferences-Sound
Thanks, but I've seen it, I've gone through it, it doesn't help.

I have followed all the steps to be found here:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

They haven't helped either...still no sound.

---

### Post by bilekbp on 2010-09-13
So here is my aplay -l and aplay -L output. Can anyone assist me in passing S/PDIF HD audio through my Nvidia Geforce 240 via the HDMI out?

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC882 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```

---

### Post by bilekbp on 2010-09-13
Ok, I have also run the following:
pactl load-module module-alsa-sink device=hw:0,1
Then using pavucontrol I am able to see the streams.

I just don't know how to configure it to work properly. While running Totem I can see an audio stream in pavucontrol, but I don't know what mixer settings to use and what Profile settings to use to get this to work.

I'm real new at this and don't have a clue as to what I'm doing :P

Edit: Can I make changes on the fly and tell if it works, or do I have to restart alsa/pulseaudio each time I make a change to test it?

---

