---
title: "Where is system info now?"
date: 2011-05-09
forum: General Help
---

### Post by ThePhysician on 2011-05-09
Can't find where 11.04 hid system info at. 

I need to know if the version of Ubuntu installed is 32 or 64 bit and other system info. No idea where they hid it in this terrible UI though. Any help?

---

### Post by jerome1232 on 2011-05-09
Well unsure of where in the ui but you can always

```
lsb_release -a
uname -m
```

lsb_release will show you what version of Ubuntu you are running
uname -m will show you the architecture you have installed, 32 bit would x86 64 x86_64

I hope this helps somewhat.

---

### Post by Frogs Hair on 2011-05-09
That program needs to be installed unless you are referring to the Gnome system monitor. If you in unity , click the shut down indicator and drop down to system settings or type sy in dash .

---

