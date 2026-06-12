---
title: "sound problem after package upgrade (ubuntu 10.04)"
date: 2010-09-22
forum: General Help
---

### Post by eugibon on 2010-09-22
Hi, I recently upgraded some packages and after the sound start to be strange, e.g. watching a movie the voices are are low while the music is really loud. 

Here some informations 

uname -a

Linux eugenia-laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

Thanks!

---

### Post by Me4oKyX on 2010-09-25
I'm currently using Ubuntu 10.04 and I got the same audio card on my laptop - Realtek ALC272 - but I can't get it to play so far. I'm new to linux so I could use all the help to solve this problem.... Everything else seems to be working fine so far. The notebook is Fujitsu Amilo Pi 3660 - any help will be very appreciated even if it's PM to me to avoid spam here. Sorry for the off topic but I was looking in the forum for a problem like mine but didn't come up with anything. Hope to solve it soon, cause this seems to be the only problem not to use over the Win7 :)

---

