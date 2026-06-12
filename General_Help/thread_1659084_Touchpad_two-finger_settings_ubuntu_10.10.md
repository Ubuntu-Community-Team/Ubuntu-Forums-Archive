---
title: "Touchpad two-finger settings ubuntu 10.10"
date: 2011-01-03
forum: General Help
---

### Post by vikkevest on 2011-01-03
Hello, can i change the behavior of my touchpad so that when i tap it with two fingers it emulates a middle mouse button click (mouse 3). Right now when I tap two fingers it emulates a right-click. Can anyone point me in the right direction?

Thanks in advance

---

### Post by iwan groznyj on 2011-01-19
You can configure the synaptics touchpad driver from the command line:
```
$ synclient TapButton2=2
$ synclient TapButton3=3
```
But this changes the mouse button emulation only temporarily.  Does anyone know a way to set this permanently?  (For example at xorg.conf.d?)

---

