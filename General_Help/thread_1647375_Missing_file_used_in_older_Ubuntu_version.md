---
title: "Missing file used in older Ubuntu version"
date: 2010-12-17
forum: General Help
---

### Post by williammanda on 2010-12-17
Previously I had setup 2 Snapstream remotes using ubuntu 7.10, see the following url:

[http://ubuntuforums.org/showthread.p...ght=snapstream](http://ubuntuforums.org/showthread.p...ght=snapstream)

The issue I'm having is a file no longer exists (/etc/modprobe.d/aliases). This file allowed for the id setup for each remote. I searched for the file but could not find it. Can someone lead me to it or another file that will serve the same purpose?

---

### Post by dcstar on 2010-12-17
> **williammanda said:**
> Previously I had setup 2 Snapstream remotes using ubuntu 7.10, see the following url:

[http://ubuntuforums.org/showthread.p...ght=snapstream](http://ubuntuforums.org/showthread.p...ght=snapstream)

The issue I'm having is a file no longer exists (/etc/modprobe.d/aliases). This file allowed for the id setup for each remote. I searched for the file but could not find it. Can someone lead me to it or another file that will serve the same purpose?
Try:
```
sudo touch /etc/modprobe.d/aliases
```

---

### Post by williammanda on 2010-12-17
I'm using 10.10 now and trying to setup what I did before.

---

