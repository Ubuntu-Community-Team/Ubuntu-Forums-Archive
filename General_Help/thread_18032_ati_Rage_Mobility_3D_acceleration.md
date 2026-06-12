---
title: "ati Rage Mobility 3D acceleration"
date: 2005-03-04
forum: General Help
---

### Post by pouchat on 2005-03-04
I follow this tutorial  [http://ubuntuforums.org/archive/index.php/t-7200.html](http://ubuntuforums.org/archive/index.php/t-7200.html)
to install my **ATI Rage Mobility P/M AGP 2x (rev 64) on my laptop**.

After successfully install mach64  (but common-module doesn't want to be install) i reboot my laptop. When i try to test if 3D acceleration is supported:
```
$ glxgears
"Error: couldn't get an RGB, Double-buffered visual"
```
```
$ glxinfo | grep render
direct rendering: No
```
but when i see the Xorg.log
```
# cat /var/log/Xorg.0.log | grep render
(II) ATI(0): Direct rendering enabled
```
Anyone can help me ??
thanks

---

### Post by krusbjorn on 2005-03-04
when i click that link, i get forwarded to micro$oft.com

?

---

### Post by pouchat on 2005-03-04
i make a mistake when i wrote the link. now it's ok.
[http://ubuntuforums.org/archive/index.php/t-7200.html](http://ubuntuforums.org/archive/index.php/t-7200.html)

---

### Post by daniels on 2005-03-04
What happens when you type LIBGL_DEBUG="verbose" glxinfo?

---

