---
title: "Wine kills x-session"
date: 2006-05-14
forum: General Help
---

### Post by ishkabob on 2006-05-14
I recently installed a fullscreen video game using cedega and it worked  like a charm.  However, when I subsequently tried to run a program (not a game) in Wine, it looks like it tries to go to fullscreen and then restarts my X-session.  I tried removing Cedega and Wine completely and reinstalling Wine.  Now, if I even run winecfg, it kills my x-session.  Any comments or help is greatly appreciated.  Thanks.

---

### Post by Crick on 2008-06-21
> **ishkabob said:**
> I recently installed a fullscreen video game using cedega and it worked  like a charm.  However, when I subsequently tried to run a program (not a game) in Wine, it looks like it tries to go to fullscreen and then restarts my X-session.  I tried removing Cedega and Wine completely and reinstalling Wine.  Now, if I even run winecfg, it kills my x-session.  Any comments or help is greatly appreciated.  Thanks.
This is happening to me unfortunately as well. I'll try a reinstall.

Edit: I tried reinstalling wine, it did not work. I had a feeling it might be the nvidia drivers, so I just changed the driver from "nvidia" to "nv" in the /etc/X11/xorg.conf, that managed to do it. I suspect that if I reinstall the legacy nvidia drivers for my old card it will work properly again.

---

