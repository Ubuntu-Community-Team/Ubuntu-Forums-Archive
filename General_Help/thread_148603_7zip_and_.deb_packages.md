---
title: "7zip and .deb packages"
date: 2006-03-22
forum: General Help
---

### Post by gos1 on 2006-03-22
hi I have to install 7zip extractor to my ubuntu 5.10 release. But I can only find the .deb package for debian at 7zip site. How can I open these kind of files. Or how can I install 7zip extractor ??

---

### Post by heimo on 2006-03-22
You can try
```
sudo dpkg -i filename.deb
```
it may or may not work, depending on dependencies. ;)

---

### Post by bluevoodoo1 on 2006-03-22
to install a deb file...

sudo dpkg -i name-of-file.deb

Edit: too slow

---

### Post by gos1 on 2006-03-22
I got error messages from that. So do you know any application which can open 7zip archieve format  ?

---

### Post by heimo on 2006-03-22
Enable [universe]("https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages") and use Synaptic to install [p7zip]("http://packages.ubuntu.com/breezy/utils/p7zip")

---

