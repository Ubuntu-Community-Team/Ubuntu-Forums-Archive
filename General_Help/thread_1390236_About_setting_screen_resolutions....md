---
title: "About setting screen resolutions..."
date: 2010-01-25
forum: General Help
---

### Post by Tidbit on 2010-01-25
Is there any way I can set a screen resolution to be consistent across newly created accounts on my computer?

Ubuntu always wants to set my resolution to 1680x1050 for new accounts that I create, but my monitor's owner manual for my monitor says it should be run at 1440x900 (it's a Samsung T220).

Is there any way I can tell my system to keep 1440x900 resolution for ALL accounts on this system without me having to configure resolution on each account individually, and each account that gets created in the future?

---

### Post by ajgreeny on 2010-01-25
You may be able to manually edit the /etc/X11/xorg.conf file to add the res you want, but exactly what is needed will depend on your graphic card and the current xorg.conf, if there is one.

---

