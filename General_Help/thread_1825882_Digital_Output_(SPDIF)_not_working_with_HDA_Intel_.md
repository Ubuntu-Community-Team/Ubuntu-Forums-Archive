---
title: "Digital Output (SPDIF) not working with HDA Intel ALC269VB"
date: 2011-08-15
forum: General Help
---

### Post by webcrawler42 on 2011-08-15
I have a shared headphone/spdif jack on my ASUS B53J and am running Ubuntu 11.04 Natty.  I am not able to get the digital spdif output to work.  I have tested the spdif out under Windows 7 and it works perfectly. Any suggestions?

aplay -L
> 
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC269VB Analog
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions


aplay -l
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


cat /proc/asound/devices
> 
  1:        : sequencer
  2: [ 0- 6]: digital audio playback
  3: [ 0- 6]: digital audio capture
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 1]: hardware dependent
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control
  9: [ 1- 3]: digital audio playback
 10: [ 1- 0]: hardware dependent
 11: [ 1]   : control
 33:        : timer


ALSA Information Script
[http://www.alsa-project.org/db/?f=609cde92a58e30f3f0d95eaf6d101790a02114ac]("http://www.alsa-project.org/db/?f=609cde92a58e30f3f0d95eaf6d101790a02114ac")

---

### Post by webcrawler42 on 2011-08-15
Got it working!

Open a terminal
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this to the bottom of the file
```
options snd-hda-intel model=auto
```

REBOOT

Under Sound Preferences > Hardware > Profile will be Digital Stereo Duplex (IEC958) and selecting that option made the digital spdif output work for me.

---

