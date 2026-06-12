---
title: "window decorations problem"
date: 2006-05-23
forum: General Help
---

### Post by melissawm on 2006-05-23
Well, i just tried to install the [Crystal GL]("http://www.kde-look.org/content/show.php?content=18983") window decoration theme to install the Crystal GL theme (also in kdelook). It didn't work. Ok, so i tried to install the old crystal color theme. Surprise surprise:

```
melissa@goedel:~/kde_decorations$ sudo dpkg -i crystal-0.9.8-ubuntu-breezy-kde3.5_0.9.8-1_i386.deb
Selecting previously deselected package crystal-0.9.8-ubuntu-breezy-kde3.5.
(Reading database ... 109238 files and directories currently installed.)
Unpacking crystal-0.9.8-ubuntu-breezy-kde3.5 (from crystal-0.9.8-ubuntu-breezy-kde3.5_0.9.8-1_i386.deb) ...
dpkg: error processing crystal-0.9.8-ubuntu-breezy-kde3.5_0.9.8-1_i386.deb (--install):
 trying to overwrite `/usr/lib/kde3/kwin3_crystal.la', which is also in package kwin-style-crystal
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 crystal-0.9.8-ubuntu-breezy-kde3.5_0.9.8-1_i386.deb
melissa@goedel:~/kde_decorations$          
```

Now, nothing works. It just gives the same "overwrite" error. Anyone? Thanks..

---

### Post by johnc4510 on 2006-05-23
Try this:
sudo dpkg-reconfigure packagename
Insert the proper package name above. This will help you reconfigure an already install package.

---

