---
title: "Cant get optical sound with my Zotac f ION"
date: 2011-09-03
forum: General Help
---

### Post by donparchami on 2011-09-03
Hi, i have been using ubuntu for almost a year and i have tried everything to get sound through my optical output. I have 5.1 through my HDMI but i want 5.1 through my Optical output so i cant get DTS from movies while playing it from XBMC. 

i am using ubuntu 11.04 and here are my outputs 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0

nes@nes:~$ aplay -L
default
Playback/recording through the PulseAudio sound server
pulse
Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
Front speakers
surround40:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Digital
IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
HDA NVidia, HDMI 0
HDMI Audio Output
dmix:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
Direct sample mixing device
dmix:CARD=NVidia,DEV=1
HDA NVidia, ALC662 rev1 Digital
Direct sample mixing device
dmix:CARD=NVidia,DEV=3
HDA NVidia, HDMI 0
Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
HDA NVidia, ALC662 rev1 Digital
Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
HDA NVidia, HDMI 0
Direct sample snooping device
hw:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
HDA NVidia, ALC662 rev1 Digital
Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
HDA NVidia, HDMI 0
Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
HDA NVidia, ALC662 rev1 Digital
Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
HDA NVidia, HDMI 0
Hardware device with all software conversions

I have no idea what these things mean, hopefully someone reading this has a better understanding of this and can help me.

---

