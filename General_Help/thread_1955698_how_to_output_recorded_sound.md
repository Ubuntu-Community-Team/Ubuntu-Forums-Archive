---
title: "how to output recorded sound?"
date: 2012-04-10
forum: General Help
---

### Post by lightsaberlesbian on 2012-04-10
I currently have my guitar hooked up through a Line6 Toneport GX.  I'm running Ubuntu 10.10.  Previously and I have no idea how I had it working such that the input from the guitar played through my speakers.  Now not quite as much.  Recording is still the same and the sounds are pretty good but I can't hear what I'm playing through my speakers.  Does anyone know how I would do this?  I tried messing around with the Sound config. menu with no luck.

---

### Post by ridetheteapot on 2012-04-10
kk using pulse audio?
```
pactl load-module module-loopback
```
that should enable 'line in' monitoring

___edit___
me and my arrow.. i mean buddy.. used to record digitally, but I haven't done it in awhile (do use this for listening to LPs while encoding them though). Just wondering how linux/pulse is doing latency-wise for you and that card. You might want to check out ubuntu-studio or the jack audio server in the future to, cause that stuff(jackd) is REALLY fun.

---

### Post by lightsaberlesbian on 2012-04-10
oh nice thanks! i also found out rakarrack did the trick too

---

