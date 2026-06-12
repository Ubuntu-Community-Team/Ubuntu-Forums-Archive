---
title: "GParted wont load, it did before?"
date: 2010-09-23
forum: General Help
---

### Post by fuzzylogic25 on 2010-09-23
I have just moved to Ubuntu from Win 7 and am already getting frustrated. GParted use to work perfectly fine (only a day ago!) but now when I try to load it, there is a tab on my taskbar at the bottom saying "GParted" then another one saying "Starting GParted" then the GParted window that comes up (which was scanning the drives) just disappear, and then the "Starting GParted" tab also disappears.

Why is this? I mean, it just disappears, doesnt open without even telling me why? This gets really frustrating. I also had another application named disklets do that. I am starting to think that this occurs with applications on ubuntu for some reason.


UPDATE - ok it ran after i removed my two usb drives. but WHY?

---

### Post by WorMzy on 2010-09-23
Next time it starts happening, run it from a terminal; it may give some indication as to what's causing it to close unexpectedly.

```
gksu gparted
```

---

