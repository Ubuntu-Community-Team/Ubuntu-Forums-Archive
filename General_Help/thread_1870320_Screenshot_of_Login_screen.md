---
title: "Screenshot of Login screen"
date: 2011-10-27
forum: General Help
---

### Post by DobsonM on 2011-10-27
I use Slim as my login manager does anyone know how to take a screenshot of the login screen?

---

### Post by tors on 2011-10-27
Perhaps you could use "xwd"

```
usage: xwd [-display host:dpy] [-debug] [-help] [{-root|-id <id>|-name <name>}] [-nobdrs] [-out <file>] [-xy] [-add value] [-frame]
```

Change to a terminal (ctrl + alt + F1) and login.
Then something like:

xwd -display localhost:0 -root -out screenshot.xpm

Then back to X again (ctrl + alt + F7)

I don't know if this works, but worth a shot perhaps :)

---

### Post by DobsonM on 2011-10-27
I will give it a shot.

---

