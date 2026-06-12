---
title: "problem with startx"
date: 2006-04-15
forum: General Help
---

### Post by jsmidt on 2006-04-15
I get these problems when I type startx.  Does anybody know what I can do?

(EE) failed to load module "evdev" (module does not exist, 0)
(EE) failed to load module "vesa" (module does not exist, 0)
(EE) failed to load module "keyboard" (module does not exist, 0)
(EE) failed to load module "mouse" (module does not exist, 0)
(EE) no drivers availiable

Fatal server error: No screens found
XIO: Fatal IO error 104 (Connection reset by peer) on x server ":0.0" after 0 requests (0 known processed) with 0 events remaining.  

Thanks

---

### Post by taurus on 2006-04-15
Since you are already at the command prompt, try to configure your X again by typing
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by jsmidt on 2006-04-15
Okay I found out I had to install a couple packages.  Does anybody know what can be done about this error:

Fatal server error: 
could not open default font 'fixed'

---

### Post by Przemekc1 on 2006-05-01
Maybe you know now what to do? I've got the same problem :(

---

