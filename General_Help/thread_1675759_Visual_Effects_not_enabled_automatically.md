---
title: "Visual Effects not enabled automatically"
date: 2011-01-26
forum: General Help
---

### Post by islander_810 on 2011-01-26
Just finished updating and I have to manually enable Advanced Visual Effects every time I login. Anyone else seeing this? Any solution?

---

### Post by sikander3786 on 2011-01-26
Which version of Ubuntu is this?

Which graphics card? Did you install any proprietary drivers?

Does it look like Ubuntu is running in safe mode whenever you cold boot?

```
lspci | grep VGA
```

```
glxinfo | grep vendor
```

---

### Post by islander_810 on 2011-01-26
I'm running Ubuntu 10.10. The card is ATI HD4850 using proprietary drivers. Nope Ubuntu is booting normally, not in safe mode.

---

### Post by realzippy on 2011-01-26
Set your compiz settings in ccsm and never touch the "desktop effects settings" given in rightclickdesktop menue,then your settings will persist
reboots.

---

### Post by islander_810 on 2011-01-26
Desktop-compositing and hence Compiz is disabled by default at login till the visual effects are enabled. Setting up compiz isn't helping

---

### Post by realzippy on 2011-01-26
> **islander_810 said:**
> Desktop-compositing and hence Compiz is disabled by default at login till the visual effects are enabled. Setting up compiz isn't helping

Desktop effects *is* compiz.

Set/enable your effects in ccsm and they will remain.

If you do not want to try this (had this problem on 2 machines (Intel and Nvidia graphics)),you could add to
Startup Applications:

```
compiz --replace
```

---

