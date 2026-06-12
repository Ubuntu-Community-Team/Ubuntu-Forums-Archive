---
title: "w32codecs"
date: 2006-03-03
forum: General Help
---

### Post by ubuntuubuntu on 2006-03-03
When I type sudo apt-get install w32codecs
, I get the following message:
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

How can I install the w32codecs?

---

### Post by knalle on 2006-03-03
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by OMRebel on 2006-03-03
You could also try using Automatix.  It worked great for me.

---

### Post by ubuntuubuntu on 2006-03-03
I followed the instructions knalle suggested, but it didn't worked.  I still get the message
sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by Jason_25 on 2006-03-03
Post your /etc/apt/sources.list

---

### Post by aysiu on 2006-03-03
Just download [this file](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb) to your desktop and go to Applications > Accessories > Terminal and type ```
cd Desktop
sudo dpkg -i w32*.deb
```

---

### Post by monkeyface on 2006-03-03
PLF's main mirror have some problems atm, use one of the others. :)

---

