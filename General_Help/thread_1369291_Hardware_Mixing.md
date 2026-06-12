---
title: "Hardware Mixing"
date: 2009-12-31
forum: General Help
---

### Post by RedSingularity on 2009-12-31
Does ALSA support hardware mixing?  I wanted to know because i am using Pulseaudio and its a little buggy.  I would like to try another sound server, if available.  Thanks.

---

### Post by RedSingularity on 2010-01-01
Bumpoooo

---

### Post by RedSingularity on 2010-01-03
Bumpooooo # 2

Anyone?

---

### Post by kostkon on 2010-01-03
If you remove PulseAudio, and IF your card supports hardware mixing (the vast majority don't) and IF the ALSA driver for your card supports it too then, yes, you'll have hardware mixing. Otherwise the ALSA software mixer will be used (called *dmix*) which is obviously inferior compared to PulseAudio.

---

