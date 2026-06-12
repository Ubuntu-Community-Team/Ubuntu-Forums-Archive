---
title: "Compiz + ccsm segfaults"
date: 2012-01-26
forum: General Help
---

### Post by yuki-nagato on 2012-01-26
All of this started after I reverted KDE4 from 4.8 (was working in 4.7 previously) back to 4.7 so something got broken I just have no idea what.
Kubuntu 11.10  KDE4.7  Compiz 1.0.9.6

output from running ccsm in Terminal:

Backend     : kconfig4
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Segmentation fault

running compiz --replace in the Terminal gives the same output.

ccsm will run if it has higher privileges (why? it shouldn't need them...) compiz still gives the same error.

avant window manager functions fine as do the native compositing effects of KDE4.

A clean reinstall of both compiz and ccsm (removed compiz-1 from .config, full uninstall, remove .compiz) did nothing.

Any ideas about what I can do to find out what could be missing/isn't right that causes compiz to segfault?

---

### Post by yuki-nagato on 2012-01-29
bump

---

