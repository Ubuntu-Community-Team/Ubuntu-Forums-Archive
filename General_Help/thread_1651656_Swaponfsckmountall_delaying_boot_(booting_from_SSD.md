---
title: "Swapon/fsck/mountall delaying boot (booting from SSD)"
date: 2010-12-23
forum: General Help
---

### Post by reablom on 2010-12-23
I recently installed an SSD (OCZ Vertex II) in my PC to speed up boottime and make applications boot faster.

The latter works fine, however I'm not too impressed with the boottime (26s according to bootchart, see attached file). 

Especially at the start mountall, fsck or swapon seems to slow down everything for about 10s.
Does anyone have a clue whether this is normal behavior?
Can I speed it up?

Edit: ok the thumbnail is illegible. See here instead: [http://img163.imageshack.us/img163/8674/hal9000maverick20101223.png](http://img163.imageshack.us/img163/8674/hal9000maverick20101223.png)

---

### Post by reablom on 2010-12-23
Swapon for the swapspace on the SSD indeed causes the delay. 
I swithced to a swapspace on my HDD and now bootchart looks like this: [http://img413.imageshack.us/img413/8674/hal9000maverick20101223.png](http://img413.imageshack.us/img413/8674/hal9000maverick20101223.png)

I don't get it. Any ideas?

---

### Post by reablom on 2010-12-25
Bump

---

### Post by reablom on 2010-12-29
Final bump.

---

