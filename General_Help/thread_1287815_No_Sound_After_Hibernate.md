---
title: "No Sound After Hibernate"
date: 2009-10-10
forum: General Help
---

### Post by seminole on 2009-10-10
Hello, I'm running Jaunty. I did a hibernate last night, turned the computer back on this morning and didn't have any sound. I searched for an issue and tried to solve it, finally rebooting the system. Now, I still don't have any sound.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$

I checked to see if my microphone was still working by using Audacity to see if I could record, as it does, but I hear no sound.

I've check cables and speakers, neither of which seem to be the problem, so I think it is in the system. I tried restarting alsa with "sudo alsa force-reload", still no sound.

Any ideas on how I can fix this? I would defiantly appreciate your help!

Thank you.

---

