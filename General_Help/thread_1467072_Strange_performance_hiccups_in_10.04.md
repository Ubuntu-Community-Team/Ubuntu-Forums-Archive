---
title: "Strange performance hiccups in 10.04"
date: 2010-04-30
forum: General Help
---

### Post by hojjan on 2010-04-30
I have these strange performance hiccups whenever I play a video, audio file, or use flash (or at least that's when I notice them). It's like the CPU halts for a second and then tries to play catch-up, causing corruption. Really annoying thing that isn't present in Kubuntu 10.04, which leads me to believe that it isn't hardware related. At first I suspected video drivers, but the hiccups persist regardless of which ones I use.

Any ideas?

---

### Post by hojjan on 2010-05-30
I've narrowed the possible processes causing this down to gdm-binary, but that's as far as I've gotten. 

Anyone got any tips on how to debug an issue such as this, now that I've concluded that the gdm daemon is behind it?

---

### Post by hojjan on 2010-06-06
Turned out it was an issue with pulse audio that others have. No fix. Resolved by replacing pulse with alsa.

---

