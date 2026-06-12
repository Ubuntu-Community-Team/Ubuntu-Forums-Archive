---
title: "Java"
date: 2006-05-07
forum: General Help
---

### Post by cssutto on 2006-05-07
If I have software using Java; Moneydance, for instance, why is it that I can not get Firefox to see Java?

It seems a waste of system resources to have a copy of java for every package that needs it.

CSSJR

---

### Post by mlind on 2006-05-07
How did you install java?

If you used debian's java-package building, there should be symlink for 
libjavaplugin.so on /usr/lib/mozilla/plugins, so firefox will find the java plugin.

see [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
for debian way to install java

---

### Post by siminone on 2006-05-07
you need to create a symbolic link to the java plugin in the firefox folder.

---

