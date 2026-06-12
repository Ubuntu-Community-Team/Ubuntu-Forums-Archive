---
title: "Sound From Internal Speakers but not Headphones"
date: 2011-01-07
forum: General Help
---

### Post by Elvensin on 2011-01-07
Hi i am running Xubuntu 10.10 on a Toshiba Satellite L645d, s4037 i get sound from the internal speakers, but dont get any sound from headphones when plugged into the jack.  I ran this to be on the safe side [http://www.alsa-project.org/db/?f=b394cbdb61e3ad438a176bdb3b6e3ee315db4a14](http://www.alsa-project.org/db/?f=b394cbdb61e3ad438a176bdb3b6e3ee315db4a14)
if anyone comes up with a way to fix this issue i will greatly appreciate it been a long time since i have used terminal so please dummy down the comments so i can get this working

Much Appreciated,
Ben

---

### Post by bytbox on 2011-01-07
Does mixer show an entry for the headphones, or does it just not seem to know they exist?

If the latter, does putting your computer to sleep (or "stand by" or whattever) and then waking it help?

---

### Post by Elvensin on 2011-01-07
in mixer headphones do not show, waking did nothing

---

### Post by r00t4rd3d on 2011-01-07
Ive been trying to help Ben get this fixed to no avail. Seems others are having the same issue with the same laptop.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/686332](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/686332)

---

### Post by Elvensin on 2011-01-07
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

term = aplay -L

---

### Post by Elvensin on 2011-01-07
elvensin@DeathsFortune:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic B',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic C',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic E',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic F',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [off]
  Front Right: Capture 80 [100%] [6.00dB] [off]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '30dB'

---

### Post by Elvensin on 2011-01-07
Conexant CX20585 << from looking around on few other sites < this is the bug not the Computer itself, others have same issue but seems this Computer may have a lot to do with it having that same card

---

