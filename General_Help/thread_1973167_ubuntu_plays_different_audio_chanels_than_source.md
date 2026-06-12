---
title: "ubuntu plays different audio chanels than source"
date: 2012-05-04
forum: General Help
---

### Post by Tossler on 2012-05-04
Hi,

I need help with configuration I've been struggling with for some time, in ubuntu 11.04 and with new release 12.04 as well. What i want is a custom configuration where output from HDMI is the same as source, 2 channels for stereo mp3's and multichanel for higher-channel audio sources, like movies in DTS.

first some information about my hardware:

```
$ aplay -l
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

```I've added the following to my /etc/pulse/default.pa file:

```
load-module module-alsa-sink device=hw:0,7
```and mapped all channels in /etc/pulse/daemon.conf

```
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe
```and in DTS audio ok, every channel plays from right speaker, but not for stereo, stereo sources play in 5.1 configuration as well, tried to play with .asoundrc config file but without success.... I'd be grateful for any tips

---

