---
title: "KDE on Ubuntu?"
date: 2005-01-24
forum: General Help
---

### Post by andrewski on 2005-01-24
Hi there all,
I got Ubuntu installed and I'm impressed! :D 

Anyway, I'm trying to get KDE installed, but when I try to install one of its components (e.g. kicker), I get failing dependencies as follows:
```
kicker:
 Depends: kdelibs4 but it is not going to be installed
 Depends: libkonq4 but it is not going to be installed
 Depends: libqt3c102-mt but it is not installable
```I look in libraries and see that libqt3c102-mt-odbc is available, but not libqt3c102-mt.

How can I resolve this dependency?

---

### Post by merc on 2005-01-24
I installed kde (only kdebase) using aptitude. And everything worked fine. You might want to try installing kicker through aptitude. See if that helps.

---

