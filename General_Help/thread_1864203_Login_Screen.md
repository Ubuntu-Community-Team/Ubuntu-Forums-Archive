---
title: "Login Screen"
date: 2011-10-18
forum: General Help
---

### Post by gupti on 2011-10-18
I have tried changing the login screen image by using Simple Lightdm Manager. It only gives me a black screen, so I uninstalled it and tried changing it manually with /etc/lightdm/unity-greeter.conf , with no avail. Any ideas?

---

### Post by zteel on 2011-10-19
i have the same problem

---

### Post by gupti on 2011-10-19
Can anyone post their non-edited "unity-greeter.conf" so we can compare it to mine?```
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# logo = Logo file to use
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/warty-final-ubuntu.png
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb
```

---

### Post by gupti on 2011-10-19
FIXED: I compared it to the unity-greeter.conf of my laptop, and the image path was incorrect ( /etc/share**/backgrounds**/warty-final-ubuntu.png).:rolleyes:

---

### Post by collisionystm on 2011-10-19
Point It towards a picture in your home folder. Bad permissions can cause the black screen

---

