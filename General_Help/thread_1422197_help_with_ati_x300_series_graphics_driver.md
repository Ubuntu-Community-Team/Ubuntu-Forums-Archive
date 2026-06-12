---
title: "help with ati x300 series graphics driver"
date: 2010-03-05
forum: General Help
---

### Post by xpiercex on 2010-03-05
hello i have a ati radeon x300 series video card and i cant get the 3d acceleration to work
for example when i try to enable desktop effects it says searching for drivers and then visual effects could not be enabled. im sorry if this sounds like a dumb question im new to linux.

---

### Post by 3rdalbum on 2010-03-05
ATI doesn't make a driver for the X300 anymore, so you're stuck with the open-source driver which *might* not allow Compiz.

You might want to just try the following. Hit Alt-F2 and type:

```
compiz --replace
```

This starts the visual effects window manager directly.

Unfortunately, if Compiz doesn't work on your graphics card, then there's not a lot you can do except complain to ATI for dropping support for your card, or buy an Nvidia graphics card.

---

### Post by xpiercex on 2010-03-05
it says error
could not open location
error stating file home/jon/compiz--replace
no such file or directory
i just installed linux a few days ago and at first it was working perfectly fine and then it just stopped i dont really know why

---

### Post by xpiercex on 2010-03-05
oops nevermind actually my screen just flickers and then nothing

---

