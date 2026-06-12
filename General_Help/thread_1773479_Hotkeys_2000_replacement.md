---
title: "Hotkeys 2000 replacement"
date: 2011-06-02
forum: General Help
---

### Post by miaerbus on 2011-06-02
At work I'm using Windows when I have HotKeys 2000 installed. I attach the list of shortcuts and there is also *.h2d file available. Is there any software that does the same in Ubuntu?

The other thing I need for my work is UltraEdit, but I can't install it on my Ubuntu 11.04 because "dependency is not satisfiable: libicu42 (>= 4.2-1)" or via terminal:

```
mia@mavrica:~/Downloads$ sudo dpkg -i uex_2.1.0.5_i386.deb 
[sudo] password for mia: 
Selecting previously deselected package uex.
(Reading database ... 143971 files and directories currently installed.)
Unpacking uex (from uex_2.1.0.5_i386.deb) ...
dpkg: dependency problems prevent configuration of uex:
 uex depends on libboost-regex1.42.0 (>= 1.42.0-1); however:
  Package libboost-regex1.42.0 is not installed.
 uex depends on libicu42 (>= 4.2-1); however:
  Package libicu42 is not installed.
dpkg: error processing uex (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 uex
mia@mavrica:~/Downloads$
```

---

