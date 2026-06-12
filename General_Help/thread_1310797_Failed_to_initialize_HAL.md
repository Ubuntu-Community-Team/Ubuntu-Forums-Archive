---
title: "Failed to initialize HAL"
date: 2009-11-02
forum: General Help
---

### Post by spacemarc on 2009-11-02
hi, after a crash i obtain on GNOME desktop an alert: "Failed to initialize HAL" without mouse nor keyboard control.

On boot etc/init.d/hal not want to start (timeout, i presume).

I've tried to /usr/lib/hal/hald-generate-fdi-cache but without success.

There are other commands that I can do?

---

### Post by spacemarc on 2009-11-02
some suggest to resolve?

---

### Post by P4man on 2009-11-02
are you using automatic login ?

---

### Post by spacemarc on 2009-11-02
yes.
The icons are displayed, the wallpaper also, but i don't have control on mouse and keyboard

---

### Post by P4man on 2009-11-02
> **spacemarc said:**
> yes.
The icons are displayed, the wallpaper also, but i don't have control on mouse and keyboard

Try disabling the autologin, set a timed login with at least 5s.

To fix the problem now, access a terminal (from recovery mode if needed) and try
```

sudo aptitude reinstall hal
```

---

### Post by spacemarc on 2009-11-02
i tried your tips but the problem is not resolved....

---

### Post by rshetye on 2009-11-15
Please look @ 

[http://ubuntuforums.org/showthread.php?t=1277364](http://ubuntuforums.org/showthread.php?t=1277364)

for the solution that I managed to cobble together...

---

