---
title: "Help - Kubuntu 9.04 - No desktop on login"
date: 2009-08-12
forum: General Help
---

### Post by Al B on 2009-08-12
Dual boot, coreduo, with 9.04 Jaunty,Kubuntu, it will boot normally but goes into terminal mode (tty 1) for login. Tried recovery mode and changed from onboard graphics, Intel, to an ati card but both the same. Machine works fine in windows. Has anybody got any suggestions.

---

### Post by NightwishFan on 2009-08-12
When you get to a command line, type this command and tell us what happens.

```
startx
```

---

### Post by Al B on 2009-08-12
> **NightwishFan said:**
> When you get to a command line, type this command and tell us what happens.

```
startx
```

Machine now freezes with coloured bands across top of screen.

---

### Post by Mi*6d@# on 2009-08-12
Try to start GNOME display manager instead of trying just to start X11 (as in most cases that fails even if everything is OK)```
sudo /etc/init.d/gdm start
```

---

### Post by Al B on 2009-08-12
> **SkyBon said:**
> Try to start GNOME display manager instead of trying just to start X11 (as in most cases that fails even if everything is OK)```
sudo /etc/init.d/gdm start
```

Entering the above appears to do nothing.

---

### Post by Al B on 2009-08-13
> **NightwishFan said:**
> When you get to a command line, type this command and tell us what happens.

```
startx
```

Having removed the  envy ati drivers and after login, startx causes the machine to freeze with an error window at the top of the screen 

kstartupconfig4 does not exist or fails.The error code is 127

---

### Post by Valok on 2009-08-13
> **SkyBon said:**
> Try to start GNOME display manager instead of trying just to start X11 (as in most cases that fails even if everything is OK)```
sudo /etc/init.d/gdm start
```

Is GNOME even installed under the normal Kubuntu installation?  I'm not sure but I don't think it is.

---

