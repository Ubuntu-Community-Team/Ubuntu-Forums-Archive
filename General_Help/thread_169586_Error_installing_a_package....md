---
title: "Error installing a package..."
date: 2006-05-02
forum: General Help
---

### Post by morbid_bean on 2006-05-02
Im trying to install the vlc movie player with the package manager and i get a damn error when i mark it for installation.


vlc:
 Depends: liba52-0.7.4  but it is not installable
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: libmodplug0c2 (>=1:0.7-4.1) but it is not installable
 Depends: libmpeg2-4  but it is not installable
 Depends: wxvlc but it is not going to be installed

now wtf!?!

---

### Post by zxee on 2006-05-02
In breezy you need to make sure your /etc/apt/source.list has nonfree depositories enabled. It seems like you're using synaptic-although you don't say-anyway you may want to update. From terminal it's 'apt-get update'

---

### Post by morbid_bean on 2006-05-02
[QUOTE=zxee]In breezy you need to make sure your /etc/apt/source.list has nonfree depositories enabled. It seems like you're using synaptic-although you don't say-anyway you may want to update. From terminal it's 'apt-get update'[/QUOTE]



how do i make sure that /etc/apt/source.list has nonfree depositories enabled?

---

### Post by SreckoMicic on 2006-05-03
If you are using synaptic see this:

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

or open source.list and uncomment (remove #) wanted repo.

---

