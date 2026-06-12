---
title: "No GUI"
date: 2009-12-28
forum: General Help
---

### Post by Akira96 on 2009-12-28
For some reason, I reboot Ubuntu and my GUI went away. I'm am not a N00b but I don't know the right command to fix it.

---

### Post by gsmanners on 2009-12-28
This is usually related to Xorg. Best bet is to check out your /var/log/Xorg.0.log (and take a good look at your /etc/X11/xorg.conf as well).

---

### Post by Admiral Yi on 2009-12-28
Try running
```
startx gdm
```

and see if that brings it back. It might, unless there is a problem with xorg as previously mentioned. Post any errors that come back.

---

