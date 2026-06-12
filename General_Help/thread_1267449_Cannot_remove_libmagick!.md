---
title: "Cannot remove libmagick!"
date: 2009-09-15
forum: General Help
---

### Post by dragos240 on 2009-09-15
I keep trying, but:
```

~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libmagick++2 libmagickcore2 libmagickwand2
0 upgraded, 0 newly installed, 3 to remove and 79 not upgraded.
3 not fully installed or removed.
After this operation, 8028kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 366605 files and directories currently installed.)
Removing libmagick++2 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libmagick++2 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing libmagickcore2 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libmagickcore2 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing libmagickwand2 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libmagickwand2 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libmagick++2
 libmagickcore2
 libmagickwand2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by zvacet on 2009-09-16
```
sudo apt-get --purge remove  libmagick++2
```

---

