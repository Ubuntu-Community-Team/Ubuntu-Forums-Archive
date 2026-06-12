---
title: "No A/52 or AC3 Audio through HDMI only Digital Stereo going through"
date: 2010-11-22
forum: General Help
---

### Post by kanazky on 2010-11-22
Hey,

My Blurays should have a DTS A/52 SPDIF and a AC3 5.1 Surround audio tracks which I know because on windows it worked perfect through HDMI. On Ubuntu I can get sound out but its **Digital Stereo** and that only offers 2 channels (which works fine for 2 channels). How do I remap my HDMI output to go from Stereo to allow surround sound tracks or even just send my receiver the raw audio.

I am using the default settings in pulse audio.
Have a ATI Radeon HD 5730 Graphics

```

jacob@jacob-Studio-Laptop:~$ aplay -L
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, ATI HDMI
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Hardware device with all software conversions

```

---

### Post by bluekarasu on 2010-12-27
Same problem here, help needed.

---

