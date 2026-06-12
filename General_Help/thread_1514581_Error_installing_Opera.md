---
title: "Error installing Opera"
date: 2010-06-21
forum: General Help
---

### Post by nemiux on 2010-06-21
When I download opera 10.10 for linux in .deb package, I can't click install, this is the message I get:
```
Error: Dependency is not satisfiable: libqt3-mt (>= 3.3.4)

``` Could someone help me how to install opera browser, please?

Thank you

---

### Post by Pollox on 2010-06-21
Odd, I think it (libqt3-mt) should be available by default.  Update your package list (using update manager would work fine) and try to find it.  If not, you can get it here: [http://packages.ubuntu.com/lucid/libqt3-mt](http://packages.ubuntu.com/lucid/libqt3-mt) (at the bottom).

Edit: It looks like you're using Jaunty, so you actually need: [http://packages.ubuntu.com/jaunty/libqt3-mt](http://packages.ubuntu.com/jaunty/libqt3-mt) .  You can search for any package at [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by SoFl W on 2010-06-23
I did a fresh install of Ubuntu 10.4,(64) I went to the Opera website and they didn't have any deb packages.   A google search found 32bit deb packages [here]("http://deb.opera.com/") but no 64 deb packages.


**UPDATE:**  Found the deb package, it lists it as "default", and I was looking for "deb"

---

