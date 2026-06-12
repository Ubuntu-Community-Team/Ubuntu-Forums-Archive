---
title: "No Sound..."
date: 2006-05-21
forum: General Help
---

### Post by metricben on 2006-05-21
I have just loaded Breezy Badger onto my PC and have limited sound.

Previously I had Debian with sound working, so this leads me to believe it is a software problem.
I have system sounds(startup/shutdown) and can play audio cd's through Totem.
I have tried a few "solutions" but they didn't work.

[B]ben@ubuntupc:~$ lspci | grep audio
0000:00:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)[/B]

i want to be able to use 4.0 sound if possible

at alsa-project.org i found a tutorial for this setup, but compiling modules and kernels and whatever is a tad beyond me

thx in advance

---

### Post by metricben on 2006-05-21
update: i can get sound working through amarok when i select xine/oss

unfortunetly i now have no sound in totem
i reckon this is what made it work:
```
ben@ubuntupc:~$ cd /lib/alsa-utils
ben@ubuntupc:/lib/alsa-utils$ ls
udev
ben@ubuntupc:/lib/alsa-utils$ sh udev
 * Setting up ALSA...                                                    [ ok ]
ben@ubuntupc:/lib/alsa-utils$

```

still need help (preferably ALSA + ill continue to test different apps)

---

