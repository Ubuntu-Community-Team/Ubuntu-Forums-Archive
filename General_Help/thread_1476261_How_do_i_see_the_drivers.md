---
title: "How do i see the drivers?"
date: 2010-05-07
forum: General Help
---

### Post by Monotoko on 2010-05-07
Hiya guys, was just wondering how i see the drivers my 10.04 install has decided to use? Mostly i was wondering which driver its used for the graphics, the default or an intel one...

---

### Post by quadproc on 2010-05-07
> **Monotoko said:**
> Hiya guys, was just wondering how i see the drivers my 10.04 install has decided to use? Mostly i was wondering which driver its used for the graphics, the default or an intel one...
A couple of thoughts:

One, if your system has an xorg.conf file then look in it for a line which contains the word Driver followed by a string in quotes.  That will be the driver.

Two, see if you can find the driver name from modprobe.  For me, this works:
```
modprobe -l | grep kernel/drivers/char/drm
```

quadproc

---

