---
title: "[B] apt-get remove leaves so much behind [/B]"
date: 2010-01-27
forum: General Help
---

### Post by stonehinge03 on 2010-01-27
Is there a way to get it to really remove packages and delete all the files that the installation created?

---

### Post by sisco311 on 2010-01-27
```
apt-get purge package
```removes the configuration files as well.

---

### Post by dearingj on 2010-01-28
There's also ```
apt-get autoremove --purge
``` which purges any dependencies which are no longer needed by any installed programs.

---

