---
title: "xubuntu 12.04 windows borders are gone"
date: 2012-04-28
forum: General Help
---

### Post by supernater on 2012-04-28
When I started xubuntu 12.04 the windows borders were gone and my windows always orient themselves at the upper left of my screen.  Switching themes does not do anything.  Also, in Settings->WindowManager the window is blank.  Any suggestions?

---

### Post by Toz on 2012-04-28
Alt-F2 then run:
```
xfwm4 --replace
```

(The window manager crashed and needs to be restarted)

---

### Post by pqwoerituytrueiwoq on 2012-04-28
are you running compiz?
if so you will need to enable them in ccsm along with everything else
if you are not using compiz see the above post

---

### Post by supernater on 2012-04-28
> **Toz said:**
> Alt-F2 then run:
```
xfwm4 --replace
```

(The window manager crashed and needs to be restarted)

That did it!  Thanks!  Ummm... what exactly did that do?

---

### Post by Toz on 2012-04-28
It restarted the window manager (xfwm4).

---

