---
title: "Dual monitors not detected"
date: 2012-07-26
forum: General Help
---

### Post by Bahawolf on 2012-07-26
Hey there!

I have 2 GTX 265 video cards and 2 ASUS monitors. Though when I go into Display, there is one monitor labeled as 'Laptop' and I can not see or enable a second monitor.

Ironically, during the installation, my monitors were detected and worked fine.

May you please point me in the right direction? I've tried toggling the NVidia drivers in the settings but that didn't resolve the issue.

Thanks!

---

### Post by dino99 on 2012-07-26
some custom xorg.conf sometimes disturb the kernel (as now it directly deal with X)
so remove or rename it if you have one, then logout/in.

otherwise, purge then reinstall nvidia*

---

