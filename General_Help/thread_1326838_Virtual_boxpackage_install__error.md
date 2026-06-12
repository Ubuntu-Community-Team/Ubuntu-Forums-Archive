---
title: "Virtual boxpackage install  error"
date: 2009-11-14
forum: General Help
---

### Post by su-37 on 2009-11-14
Hey, my dad was installing a new version of virtual box after having removed the ose version. When he opens the deb manager window the following comes up and we were wonder what we could do to fix it? We have checked installed apps and its not there as installed.

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
There is a repo for the latest virtualbox 3.0.10 that you can add and install from. [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Try uninstalling the virtualbox and virtualbox-ose packages and then use the site above to add the repo and install.

oops just saw that you looked for the ose package. Try ```
sudo whereis virtualbox
``` and deleting what's installed.

---

