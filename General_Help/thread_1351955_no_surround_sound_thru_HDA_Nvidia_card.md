---
title: "no surround sound thru HDA Nvidia card"
date: 2009-12-11
forum: General Help
---

### Post by xjgnsdof on 2009-12-11
I have a Zotac Ionitx A-U mobo, which has a built-in 5.1 sound card. I am running Xubuntu 9.10 (32-bit).

I only get sound in my front left and front right speakers. I know the card has the capability; how do I configure this machine for surround sound?

---

### Post by xjgnsdof on 2009-12-11
up

---

### Post by xjgnsdof on 2009-12-11
up

---

### Post by jatarn on 2010-01-19
i have the same setup and the same problem. Does anyone know how I can enable surround sound, there isn't a surround profile only stereo.

---

### Post by raven88 on 2010-09-27
Hi,

I have the exactly same problem. I tried everything found on the Internet:
-Commented out this line "default-sample-channels = 6" in /etc/pulse/daemon.conf
-compiled from the source different ALSA driver.
-used .asoundrc for Pulseaudio to make upmixing for stereo mp3 Files
-edited /etc/modprobe.d/alsa-base.conf

Ouptut of "aplay -l"
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Ouptut of "aplay -L"
```
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC268 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers

```Output of "cat /proc/asound/cards"
```

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf0880000 irq 21

```I´m running Ubuntu10.04 on an Acer Aspire 7520G. I think these bug is ALSA related not (X)Ubuntu.

---

