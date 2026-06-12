---
title: "SigmaTel STAC 9205: Headphone Jack"
date: 2009-07-21
forum: General Help
---

### Post by mudcat on 2009-07-21
Basically my laptop speakers work, but as soon as I plug in my headphones there is no sound at all. Has anybody found a solution to this error?

---

### Post by mudcat on 2009-07-21
Actually just fixed this myself... upgrade to the new alsa driver 1.0.20 and edit your alsa.conf file by adding [FONT=monospace]"[/FONT]options snd-hda-intel model=eapd position_fix=1" below the text. After a quick reboot everything should work.

---

