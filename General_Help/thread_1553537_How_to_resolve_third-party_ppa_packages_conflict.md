---
title: "How to resolve third-party ppa packages conflict?"
date: 2010-08-15
forum: General Help
---

### Post by WinterWeaver on 2010-08-15
I need to install some packages, but it fails because I previously installed gnome-shell testing, and now have the ricotz ppa packages conflicting with the default packages. See error below.

```
libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.20.1-0ubuntu2) but 2.20.1-0ubuntu3~10.04~ricotz2 is to be installed
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libatk1.0-dev but it is not going to be installed

```

How do I remove these packages and re-install the default ones, without risking damage to my system?

UPDATE: I have now tried to remove this packages using ppa-purge and the new ubuntu tweaks, but for the life of me I cannot get rid of them.

---

### Post by WinterWeaver on 2010-08-16
Bump

---

### Post by WinterWeaver on 2010-08-16
See the attached image for the 3 packages. I have removed the ricotz ppa completely now and these packages are still sitting there not being updated.

It's driving me nuts. please help :(

---

