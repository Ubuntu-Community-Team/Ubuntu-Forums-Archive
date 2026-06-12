---
title: "flash-plugin problem"
date: 2010-02-20
forum: General Help
---

### Post by m4tic on 2010-02-20
```
dpkg: error processing adobe-flashplugin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

```

Now i can't install anything, i am using Kubuntu 9.10, and have tried fixing this with aptitude and nothing works. any ideas?
these are some of the things i tried. ```
sudo dpkg --clear-avail
sudo dpkg configure -a
sudo dpkg --remove adobe-flashplugin
sudo dpkg --install adobe-flashplugin
```

---

### Post by m4tic on 2010-02-20
bump

---

### Post by lovinglinux on 2010-02-20
Try

```
sudo apt-get --reinstall install adobe-flashplugin && sudo apt-get purge adobe-flashplugin
```

To install flash again...

For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

