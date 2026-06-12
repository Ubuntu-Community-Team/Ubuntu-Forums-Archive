---
title: "No sound from speakers, but all other sound works"
date: 2009-10-30
forum: General Help
---

### Post by chaosrl on 2009-10-30
Hey everyone,

I just installed Karmic on a brand new HP ProBook 5310m and I didn't realize I had no sound until I wanted to listen to some music. Thing is, I get sound through headphones, and my built-in mic works, but no sound at all through the internal speakers.

Output of aplay -l is:

```
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've tried adding options snd-hda-intel model=hp and options snd-hda-intel model=3stack to the alsa-base.conf file, but nothing changed at all in the volume preferences or sound playback. Anyone know a fix for this? Thanks!

Jeff

---

### Post by Madox.Net on 2009-11-18
In
```
/etc/modprobe.d/alsa-base.conf 
```
Add line
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

This gives me the speakers and microphone two... no microphone one...but I can live with that...

Will be collating a page on how to get this 5310m working :)

---

