---
title: "Gimp doesn't open"
date: 2010-01-17
forum: General Help
---

### Post by carlosgs91 on 2010-01-17
.

---

### Post by n0dix on 2010-01-17
Try this:
```
sudo apt-get update ; sudo apt-get purge gimp libgegl* libbabl* ; sudo apt-get install gimp ; sudo apt-get clean
```

---

### Post by carlosgs91 on 2010-01-18
.

---

### Post by konqueror7 on 2010-01-18
have you added its repo?
```
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main 
deb-src http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main

```

update and install libbabl-0.0...

---

### Post by jjyoder on 2012-02-17
Thanks n0dix! That worked for me. :D

jjyoder

---

