---
title: "Xorg.Conf file ignored."
date: 2009-12-01
forum: General Help
---

### Post by DanielPal on 2009-12-01
Hello I am using latest ubuntu(karmic something). Anyway I saw that the xorg.conf is not there by default, but I needed some custom config, so I went ahead and created one under /etc/X11/xorg.conf.
The problem is however that this xorg.conf file is not being enforced, its seems to ignore it completely, and from what I read this is something lots of people are having trouble with.
Is there any way to force this Xorg to read this conf always?

---

### Post by blueridgedog on 2009-12-01
It may be trying to parse it, but getting errors.  You should look in /var/log/Xorg.0.log for errors.

---

### Post by Leppie on 2009-12-01
What settings are you trying to customize?

---

