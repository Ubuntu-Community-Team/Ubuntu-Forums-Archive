---
title: "ubuntu 12.04 X session problem"
date: 2012-05-02
forum: General Help
---

### Post by anspectrum on 2012-05-02
Hey All,

Ive recently upgraded to 12.04 from natty and its working all right however, there is a little problem.

Ubuntu is started pretty all right in GUI mode (ive disabled unity and uses classsic interface). But then when I start another X session (ALT+Ctl+F1 ...... and then command "startx -- :2") ubuntu switches to it but kinda gets glitchy and nothing much is visible except glitched Desktop. Not even menus or notification bar, bottom bar ....nothing is visible.

This problem was not there in natty. My hardware is DELL LAtitude E6410, core i5, 2GB RAM. (HW detail is attached)

Any ideas ...?

---

### Post by anspectrum on 2012-05-07
Bump [-o<

---

### Post by anspectrum on 2012-05-28
> **anspectrum said:**
> Bump [-o<


](*,)

---

### Post by anspectrum on 2012-06-17
After a lot of frustration and hit and trials...............I switched to lightgdm and wola xserver is fixed.

to switch or reconfigure gdm

sudo dpkg-reconfigure gdm

Hope it would help.

---

