---
title: "Can't reenable visual effects"
date: 2009-07-17
forum: General Help
---

### Post by tcpa41 on 2009-07-17
Hello,today i encountered a weird problem which is that after setting visual effects from normal to none i cannot put them back to normal,when i try to do so i get this error: Desktop effects could not be enabled     Any ideas on how to fix this one?

card nvidia geforce mx400 with drives installed
ubuntu 9.04 64bit

My xorg.conf

```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

---

### Post by CatKiller on 2009-07-17
Having a tick in the /apps/metacity/general/compositing_manager key in gconf-editor can cause this behaviour.

---

