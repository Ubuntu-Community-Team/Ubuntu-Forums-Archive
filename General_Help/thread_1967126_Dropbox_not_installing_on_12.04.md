---
title: "Dropbox not installing on 12.04"
date: 2012-04-27
forum: General Help
---

### Post by DaComboMan on 2012-04-27
Have tried to install Dropbox via Software Center and i'm sent to Dropbox website for further instructions...
Try to install 32 bit (which presume fits for my Windows 7 Home Ed) and i get 'can not install 'python -gtk2 i386'

---

### Post by LemursDontExist on 2012-04-27
What package did you try to install, and are you on a fresh install, or an upgrade?

I've just done a fresh install (64 bit) and
```
sudo apt-get install nautilus-dropbox
```
worked fine, for what's it's worth.

---

### Post by amordeastrum on 2012-04-27
I was able to install Dropbox on 12.04 alpha using the same method described by LemursDontExist.
And you could have 64 bit Ubuntu while having 32 bit Windows installed on the machine.
So if you are downloading it from the website, download the correct one for your ubuntu install.  trying ```
uname -m
``` will say ```
x86_64
```if you are running 64bit version of Ubuntu.

---

