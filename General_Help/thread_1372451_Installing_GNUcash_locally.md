---
title: "Installing GNUcash locally?"
date: 2010-01-04
forum: General Help
---

### Post by liquidcross on 2010-01-04
My girlfriend has a PC running Ubuntu 9.10, but it's not hooked up to the internet. I want to install GNUcash on her system; it's in the repositories, but I obviously can't get to them on her system without a network connection. Is there any way to download the necessary files, slap them on a flash drive or whatever, and install them that way?

---

### Post by andrewc6l on 2010-01-04
Many package managers have a "download-only" option you could use - the packages (.deb) will be put in /var/cache/apt/archives. If you do:
```
sudo aptitude --download-only install gnucash
```
on a machine that's on the net, you can then copy those packages from /var/cache/apt/archives/ to the other machine. (Note that that directory will contain all packages you've downloaded, not just the ones for gnucash - you'll need to pick and choose.) Then you can use ```
dpkg -i packagename
``` to install the .deb files.

If you don't have a machine that's similar enough, you'll have to go hunting for the right versions.

---

### Post by liquidcross on 2010-01-04
My laptop's also running 9.10, so I think this will work! Thanks!

---

### Post by bodhi.zazen on 2010-01-04
You can also look at aptoncd

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

