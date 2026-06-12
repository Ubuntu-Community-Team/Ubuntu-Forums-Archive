---
title: "Primary displaayy..."
date: 2010-07-30
forum: General Help
---

### Post by Timn96 on 2010-07-30
Hey guys, I've just put Ubuntu on my new laptop as well as Windows 7, and I'm in Ubuntu at the moment, and I have an external screen hooked up, a 1080p 22" LG. I'm dual screening it with my laptop (extended desktop), but at the moment - the laptop is the primary display, how can I change this?

My xorg.cong:

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

```

And also, I'm new to the Ubuntu forums - I will hopefully be an active member :D

---

### Post by dino99 on 2010-07-30
you need to run the config tool aticonfig and check driver activation: system admin hardware driver

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

