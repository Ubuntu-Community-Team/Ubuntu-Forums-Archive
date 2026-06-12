---
title: "Login screen won't load"
date: 2009-07-16
forum: General Help
---

### Post by jonesa3 on 2009-07-16
Hello!

I've tried looking for this on the forums and elsewhere, but couldn't find an answer.

Basically, after a recent upgrade, it looks like the xserver simply won't load.  I don't get any text on the screen or error messages, but it tries to load the login screen, but only some garbled stuff appears at the top of the screen.

I have an ATI Radeon hd3650 if that helps.

Any suggestions would be appreciated.

If anyone could even point me in the right direction, that would be super.

---

### Post by jonesa3 on 2009-07-16
Ok, I figured out that the server simply won't load at ALL when i put in the Bus id for the device at pci 1@1:0:1
When I put 1:0:0, i get some garbled image at the top of the screen, and I can't do anything from there.

This is frustrating.  

I've been using fglrx, so maybe that has something to do with it?

---

### Post by jarrah-95 on 2009-09-01
this may not be the same problem as what i just had but possably if you uninstall glib from a terminal (press ctrl alt f2) 
```

sudo apt-get purge glib 

```
but if that uninstalled anything and the system still doesent load then reinstall it using 
```

sudo apt-get install glib

```
hope it works 
good luck

---

