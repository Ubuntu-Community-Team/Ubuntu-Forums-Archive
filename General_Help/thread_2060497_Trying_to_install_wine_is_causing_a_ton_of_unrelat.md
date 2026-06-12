---
title: "Trying to install wine is causing a ton of unrelated stuff to get uninstalled. Why?!"
date: 2012-09-20
forum: General Help
---

### Post by jgcsd on 2012-09-20
```

*sudo apt-get install wine*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 libbabl-0.0-0 libgegl-0.0-0 pax rpm librpmbuild2 lib32z1
  librpmsign0 ncurses-term
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64 wine1.4-common
  wine1.4-i386:i386 winetricks
Suggested packages:
  dosbox
Recommended packages:
  gettext:i386
[B]The following packages will be REMOVED
  alien debhelper gettext google-earth-stable intltool-debian lsb-core
  po-debconf[/B]
The following NEW packages will be installed
  wine wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64 wine1.4-common
  wine1.4-i386:i386 winetricks
0 upgraded, 8 newly installed, 7 to remove and 0 not upgraded.
Need to get 72.1 MB of archives.
After this operation, 132 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```The first line is the command I typed, and the bolded part is where it's warning me about removing stuff. Doing the same thing through synaptic produces the same result. What's going on?

---

