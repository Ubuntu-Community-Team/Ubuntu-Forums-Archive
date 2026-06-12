---
title: "How to make a *.deb"
date: 2010-12-21
forum: General Help
---

### Post by quietplease on 2010-12-21
am trying to make a deb to install 64bit wine. I've written a script to compile and install a shared 32-bit 64-bit wow installation of wine.

Now how do I turn this into a deb file?

---

### Post by lykwydchykyn on 2010-12-21
There are basically two ways.  The first, simplest way, is to use "checkinstall".  You can install checkinstall from the repositories.  Basically, where you'd type "make" and "make install", just type checkinstall instead.  This will make a deb and install the software into your package management system.

Checkinstall debs aren't "packaged for resale" you might say (they don't contain all the dependency information and other things), so they're ideal for when you want to compile things for your own machine, but aren't going to distribute the .deb.

The proper way to create a deb is a bit more involved, you might start here:
[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)

---

