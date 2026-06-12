---
title: "Error in Update"
date: 2010-02-11
forum: General Help
---

### Post by mattsweegold on 2010-02-11
Hey everybody,I was wondering how to fix the 404 error at [http://live.debian.net](http://live.debian.net) etch/main Packages
and the failed to fetch at [http://live.debian.net/debian/dists/etch/main/binary-amd64/Packages.gz](http://live.debian.net/debian/dists/etch/main/binary-amd64/Packages.gz)

---

### Post by jken146 on 2010-02-11
If you look in [http://live.debian.net/debian/dists/](http://live.debian.net/debian/dists/) there is no etch directory there. The current stable release is lenny.

---

### Post by mattsweegold on 2010-02-11
So then where do I go from here to remove the error. I am pretty new to Linux.

---

### Post by plucky on 2010-02-11
> **mattsweegold said:**
> So then where do I go from here to remove the error. I am pretty new to Linux.

Open a terminal **Applications > Accessories > Terminal** and post output of ```
cat /etc/apt/sources.list
```

Basically you have to get rid of that repository from your sources.list.

Or Open **System > Administration > Software Sources** and un-tick the box for that repository.

Good Luck

---

