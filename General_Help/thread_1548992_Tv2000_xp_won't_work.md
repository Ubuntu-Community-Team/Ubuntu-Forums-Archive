---
title: "Tv2000 xp won't work"
date: 2010-08-09
forum: General Help
---

### Post by nidzo732 on 2010-08-09
I have a "WinFast tv2000 xp global" tv card. I can't get it work.
Video4Linux control panel detects it but tvtime and xawtv won't work.
i've put a pile called bttv in /etc/modprobe.d/ and i put


options bttv radio=0 card=34 tuner=24 gbuffers=8

in the file. When i use modprobe | bttv i get this

WARNING: All config files need .conf: /etc/modprobe.d/bttv, it will be ignored in a future release.

Dmesg | grep bttv displays this
[   22.690581] bttv: driver version 0.9.18 loaded
[   22.690584] bttv: using 8 buffers with 2080k (520 pages) each for capture.
 Any help?

---

### Post by nidzo732 on 2010-08-09
Any help here?!?

---

