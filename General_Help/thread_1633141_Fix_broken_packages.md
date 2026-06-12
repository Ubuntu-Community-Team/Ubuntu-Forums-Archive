---
title: "Fix broken packages?"
date: 2010-11-28
forum: General Help
---

### Post by Dustin2128 on 2010-11-28
I've been trying to install trinity for some time, but I've now got 2 broken packages. I hit 'fix broken packages' in synaptic, but it doesn't seem to work. How would I manually fix them?

When I try to reinstall, I get this output:
```

E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.10.dfsg.1-3ubuntu2.10.04.1_all.deb: trying to overwrite '/etc/kde3/colors/40.colors', which is also in package kdelibs-data-kde3 4
E: /var/cache/apt/archives/kdelibs4c2a_4%3a3.5.10.dfsg.1-3ubuntu2.10.04.1_i386.deb: trying to overwrite '/etc/kde3/khotnewstuffrc', which is also in package kdelibs-data-kde3 4

```

I should really stop posting, I fixed it by installing with the command sudo aptitude install kubuntu-desktop-kde3 and skipping the broken packages. Issue still stands, answer me if you like. Posted from my joyously working KDE 3.5 desktop.

---

