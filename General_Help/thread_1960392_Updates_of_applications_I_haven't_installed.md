---
title: "Updates of applications I haven't installed"
date: 2012-04-17
forum: General Help
---

### Post by ayozito on 2012-04-17
Why I get updates from applications that I haven't installed?

For example just got and update of brasero, and I haven't it.

---

### Post by timgood on 2012-04-17
Brasero is part of the default installation of Ubuntu. Did you uninstall it? If you didn't, then you do have it.

---

### Post by ayozito on 2012-04-17
Of course it is uninstalled...

---

### Post by snowpine on 2012-04-17
In the terminal, type:

```
which brasero
```

If the answer is something like **/usr/bin/brasero** then Brasero is installed and you should accept the update. :)

---

### Post by 3rdalbum on 2012-04-17
> **ayozito said:**
> Why I get updates from applications that I haven't installed?

For example just got and update of brasero, and I haven't it.

If you didn't remove all the Brasero packages you may still be offered updates for the ones that remain. For instance, if you removed only the "brasero" package, you may still have "brasero-common" installed, and it will still get updates until you remove that package too.

---

### Post by ayozito on 2012-04-18
> **3rdalbum said:**
> If you didn't remove all the Brasero packages you may still be offered updates for the ones that remain. For instance, if you removed only the "brasero" package, you may still have "brasero-common" installed, and it will still get updates until you remove that package too.

Was this. Fault of the ****** Ubuntu Software Center. I installed back synaptic and I saw that common package.

---

### Post by HiImTye on 2012-04-18
open a terminal (ctrl+alt+t) and enter this
```
sudo apt-get autoremove
```
it will remove (most) packages that are no longer necessary

---

