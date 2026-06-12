---
title: "alsa-utils compilation"
date: 2009-12-28
forum: General Help
---

### Post by shariefbe on 2009-12-28
Hello,
    I am trying to compile the file called alsa-utils". in that i am getting some errors

```
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -L/mnt/freescale/nfs-develop/usr/local/lib/ -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
Configuration of glib library  has failed
sharief@sharief-desktop:/mnt/freescale/sources/alsa-utils-1.0.22$
```please help me

---

### Post by Zoot7 on 2009-12-28
There is a nice upgrade script posted here:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

That'll take care of everything for you, I'd try that before I'd go compiling from source directly. ;)

---

