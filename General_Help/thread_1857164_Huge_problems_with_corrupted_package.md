---
title: "Huge problems with corrupted package"
date: 2011-10-09
forum: General Help
---

### Post by Vinilguy on 2011-10-09
Every time I install or remove something, this package: kdebase-runtime always reports the same error. I tried upgrading, reinstalling, and removing the package, always unsuccessful. I get this when installing anything:
```
Setting up kdebase-runtime (4:4.4.5-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdebase-runtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up toonloop (2.1.14-1~lucid~ppa1) ...

Errors were encountered while processing:
 kdebase-runtime
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Thanks in advance.

---

### Post by hollowsyndicate on 2011-10-09
type this in to the terminal 

sudo apt-get install -f

---

### Post by Vinilguy on 2011-10-09
Got the same:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up kdebase-runtime (4:4.4.5-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdebase-runtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 kdebase-runtime
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by hollowsyndicate on 2011-10-09
dunno then lol. i dont use kde.

---

### Post by Vinilguy on 2011-10-09
:(

---

