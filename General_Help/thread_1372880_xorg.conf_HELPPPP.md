---
title: "xorg.conf HELPPPP"
date: 2010-01-05
forum: General Help
---

### Post by Ilmatic on 2010-01-05
I've been trying for very long now to adjust my screen resolution to my desired setting. So far, no luck. Just today I went in to examine what my xorg.conf looked like and this is what I saw.


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection



HELPPPPP!!!

---

### Post by dcstar on 2010-01-05
> **Ilmatic said:**
> I've been trying for very long now to adjust my screen resolution to my desired setting. So far, no luck. Just today I went in to examine what my xorg.conf looked like and this is what I saw.
........

What is wrong with the GUI tool?

---

### Post by Ilmatic on 2010-01-05
**Never mind folks. It's all good now. LOL. I just had to edit the refresh rates of my monitor. Mannnn ubuntu is a beautiful masterpiece when set to the right resolution. ; )**

---

### Post by zaphod777 on 2010-01-05
> **Ilmatic said:**
> **Never mind folks. It's all good now. LOL. I just had to edit the refresh rates of my monitor. Mannnn ubuntu is a beautiful masterpiece when set to the right resolution. ; )**

Yup... although I haven't had to touch xorg.conf in ages the latest versions of Ubuntu seam to work pretty well with the GUI tools.

---

