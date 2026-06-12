---
title: "nvidia x11 configuration report Virtualbox"
date: 2009-11-25
forum: General Help
---

### Post by Gary Nored on 2009-11-25
Ubuntu 9.10, Virtualbox 3.0.12, Windows 7, Acer X243W monitor at 1920x1200 resolution.

Got the nVidia driver running and the Ubuntu screen is beautiful! But Windows7 thinks I have a generic non PnP monitor and asserts an incorrect resolution. 

nVidia writes an xorg.conf, but doesn't really fill it in correctly. For example, nVidia knows the monitor model and resolution, but does not include this data in the xorg.conf file.

Anybody know if the Virtualbox server uses this file to decide what to tell the guest machine? If so, can I correct this file without hosing Ubuntu?

I thought the assigned resolution would be ok, but unfortunately, menu items in applications disappear under one another, so this issue really must be solved.

TIA
Gary

---

