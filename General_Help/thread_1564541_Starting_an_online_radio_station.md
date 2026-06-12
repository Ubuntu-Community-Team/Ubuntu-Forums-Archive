---
title: "Starting an online radio station"
date: 2010-08-30
forum: General Help
---

### Post by ki4jgt on 2010-08-30
Hey guys, I'm starting my own online broadcast station. Hoping to make it live for about 4 hours a day. Right now, I'm running it from my laptop. My only problem is that I need to route my audio from my speakers into my microphone. I'm thinking I use JACK for that, but the last time I tried it, it didn't turn out so well.

Can someone give me a step by step of how to route my audio through my mic?

---

### Post by tgalati4 on 2010-08-30
What type of soundcard on the laptop?

```
aplay -l
```

Some sound cards have a "monitor" switch in the "options" panel.  Try pavucontrol and see if you can find the switch.  It looks like "Input Devies", "Monitor ICH6" or similar.

---

### Post by ki4jgt on 2010-09-01
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

****EDIT: and no, I didn't see a ich6 or anything like it

---

