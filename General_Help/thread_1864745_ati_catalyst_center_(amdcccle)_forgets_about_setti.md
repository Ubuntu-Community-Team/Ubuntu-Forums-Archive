---
title: "ati catalyst center (amdcccle) forgets about settings on reboot"
date: 2011-10-19
forum: General Help
---

### Post by gruadp on 2011-10-19
I've a dual-monitor-setup and I setup the left monitor to 1280x1024 and the right monitor (widescreen) to 1680x1050 which brings a virtual desktop of 2960x1050.

Working fine, but as soon as I log out, both monitors are back to 1280x1024 which is complete wrong ratio on my right widescreen-monitor.

any idea?

thnx,
p

---

### Post by aeiah on 2011-10-19
have you tried launching it with root privileges?

---

### Post by gruadp on 2011-10-19
> **aeiah said:**
> have you tried launching it with root privileges?

I already had started as root the first time. 

I suspect that it might have something to do with the fact that the virtual desktop is 1050 high and the left screen only has 1024 height.  This wasnt a problem in 10.10 and 11.04 (I just didnt see the lower 26pixels on the left screen which is hardly noticable and there is no other way to bring my screens together)

thnx for any help,
p

---

### Post by gruadp on 2011-10-20
solved:

see step4 in [http://www.goldfisch.at/knowwiki/howtos/ubuntu_11.10#multi-display-setup](http://www.goldfisch.at/knowwiki/howtos/ubuntu_11.10#multi-display-setup)

its very important to open displays from system-settings and click apply after setting the desktop in amdcccle

p

---

