---
title: "Xserver issue"
date: 2006-05-31
forum: General Help
---

### Post by InsanePenguin08 on 2006-05-31
Has anyone come up with ways to fix the error that comes up when upgrading from Breezy to Dapper?  I mean the error about the gdm not being properly configured.  I've tried changing the graphic card driver name in sudo nano /etc/X11/xorg.conf, but nothing seems to work.

If I can't fix this, can anyone tell me how to backup all my files from Breezy so that I can reinstall Breezy without losing all my settings and such?

Thanks, help is GREATLY appreciated!

---

### Post by ash211 on 2006-06-01
What is the exact error message you're getting, and where in the boot process is it happening?

---

### Post by Kevin on 2006-06-01
While you're at it you could try sudo dpkg-reconfigure gdm ... You never know

---

