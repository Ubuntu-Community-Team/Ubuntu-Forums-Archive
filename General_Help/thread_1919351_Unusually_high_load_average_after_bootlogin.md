---
title: "Unusually high load average after boot/login"
date: 2012-02-02
forum: General Help
---

### Post by Mahkoe on 2012-02-02
All of a sudden, my Ubuntu 10.10 64 bit install is taking much longer to boot, has unusually high load average, and is laggy and unresponsive for about two minutes thereafter. Then, after about 10 minutes, the load average goes slowly back down to normal and my system is as fast as it ever was. I'm fairly sure this started after I updated my linux kernel version (to 2.6.35-32), but when I boot into the older kernel version, (2.6.35-31) I still have the same problem. On top of that (I don't know if it's related) my compiz settings keep resetting themselves.

I don't have a single clue what is causing this behaviour, but I'm hoping someone else will.

Extra information:

Hardware:
Intel i3
4GB DDR3 RAM
Intel HD Graphics
Atheros wifi card
Broadcom ethernet


About 6 months ago I updated my ubuntu version, but didn't like it, so I copied my home folder from the updated version into a brand new install of 10.10. The first system was 32 bit.

This also started around the same time I installed lxde and xfce.

---

### Post by Mahkoe on 2012-02-23
It turns out ironically that the panel applet to monitor resource usage was causing the lag.

---

### Post by HeroOfCanton on 2012-02-23
Now that's funny! :D Glad you got it figured out.

---

