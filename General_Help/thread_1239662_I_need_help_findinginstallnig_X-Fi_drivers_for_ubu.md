---
title: "I need help finding/installnig X-Fi drivers for ubuntu 9.04"
date: 2009-08-13
forum: General Help
---

### Post by Grain of Rice on 2009-08-13
As you might have already known, I am new to ubuntu. I want to get familiar with ubuntu because I did not like my previously used OS, Vista. 

Anyhow, I would like to know where to get X-Fi extreme audio drivers for ubuntu, if there are any. I also used a terminal command to list playback hardware, and this is what I got.

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
andrew@andrew-desktop:~$ 

My X-Fi device is not recognised. Though, I am able to get audio but the quality is horrible. So if you can help me find a stable driver, I would greatly appreciate it. :lolflag:

---

### Post by P4man on 2009-08-14
X-Fi support is terrible. Creative tried for years to make their own linux driver, and finally gave up and did what they should have done in the first place: open up their specifications so the linux community could write drivers. These now exist but are still experimental and quite rough, so you may be in for a rough ride.

I suggest you google on "jaunty x-fi" you'll find tons of threads. But if you got a different soundcard or onboard sound, the best solution is probably using that and think twice before buying anything from creative again :)

---

