---
title: "/usr/X11R6 ... missing?"
date: 2010-03-21
forum: General Help
---

### Post by J05HYYY on 2010-03-21
hello,

I am trying to install some software which relies on xorg. It is searching for /usr/X11R6 but this does not exist.

Does it exist somewhere else on my system and if so would it be possible to create some kind of symlink to allow the installation?

---

### Post by asmoore82 on 2010-03-21
I think you can symlink it to "/usr/lib/xorg"
```
sudo ln -s /usr/lib/xorg /usr/X11R6
```
I believe I had to do this for an ATI install a couple years ago.

Such software is extremely out of date.
The X.Org Foundation's last major X11R6 release was on December 21, 2005.
X11R7.1 was released on May 22, 2006: _[[COLOR="Purple"]http://en.wikipedia.org/wiki/X_Window_System#The_X.Org_Foundation[/COLOR]]("http://en.wikipedia.org/wiki/X_Window_System#The_X.Org_Foundation")_

---

### Post by J05HYYY on 2010-03-22
I tried it but it didn't work. I am attempting to install the pkgsrc package, x11-links:

```
=> Verifying reinstall for ../../pkgtools/x11-links
ERROR: This package has set PKG_FAIL_REASON:
ERROR: pkgsrc has been configured to use a system provided X11 installation
ERROR: but one could not be found. Possible solutions:
ERROR: 
ERROR: 	*) install X headers and libraries in X11BASE (currently /usr/X11R6)
ERROR: 	*) set X11_TYPE=modular in mk.conf to use X11 from pkgsrc
ERROR: 
ERROR: Please note that changing the value of X11_TYPE in existing
ERROR: pkgsrc installations is not supported!
```

---

### Post by J05HYYY on 2010-04-03
never mind, x11 is installed in /usr/

---

