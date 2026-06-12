---
title: "White screen, no login, sad"
date: 2009-11-01
forum: General Help
---

### Post by zygut on 2009-11-01
I had to do an init=/bin/bash to reset my password, and now when I boot instead of getting the login screen after the ubuntu splash screen, I just get a white screen and no login! I can go to the shell using cntrl-alt-f1 and login there. Disk space is fine. I tried removing the compiz stuff because I read somewhere that could cause it, but that didn't help. I did a grep EE /var/log/Xorg.0.log and it shows me:

(EE) CHROME(0): Unknown Card-Ids (3371|103C|3030); please report to
openchrome-users
(EE) [drm] drmOpen failed.
(EE) CHROME(0): [dri] DRIScreenInit failed. Disabling DRI

:(

---

### Post by zygut on 2009-11-01
Seems the xorg.conf got corrupt... dpkg-reconfigure -phigh xserver-xorg remade a functional one

---

