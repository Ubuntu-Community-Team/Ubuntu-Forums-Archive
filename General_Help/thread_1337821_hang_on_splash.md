---
title: "hang on splash"
date: 2009-11-25
forum: General Help
---

### Post by Poyntz on 2009-11-25
ok. this is a weird error. i haven't reported it yet because i know a temporary workaround, but it's not the best that i have to use it.

basically, when I start up, it shows me a splash screen which hangs. (you'd expect the login screen to show first, then the splash screen). instead i get a splash screen which doesn't finish loading.

so my workaround, i flip open a console, login, and restart kdm.
ie,
```
sudo /etc/init.d/kdm restart
```

subsequently the login screen appears, i log in, the splash screen appears, the desktop appears (etc, all like it should).

the thing is, i shouldn't have to type in this command every time I start up, it should load the login screen first, then the splash (and finish each process rather than hang).

attached are syslog entries from a "boot" string search of syslog. don't know how much help they will be...
(i couldn't attach the whole file because it's bigger than the forum upload will allow)

---

### Post by Poyntz on 2009-12-12
ok. the error only seems to be a problem when dual booting.
and if the menu.lst file is read from the partition of another OS

---

