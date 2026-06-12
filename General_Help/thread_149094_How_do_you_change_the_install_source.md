---
title: "How do you change the install source?"
date: 2006-03-23
forum: General Help
---

### Post by superami on 2006-03-23
Is there anyway to change the installation source where Ubuntu looks for packages after the install?  I would like to simply install from the DVD, but then copy the DVD to the hdd and have Ubuntu look to the hdd when I want to install a different package.  I hate always having to fish out DVDs, because I forgot something trivial.

I've done this (and network installs) with Suse for quite a while, and I simply couldn't seem to get Ubuntu to allow this.  Which, besides being annoying for the systems with DVD drives, makes Ubuntu fairly hard to install and maintain on my system without a DVD drive.

---

### Post by lnxpwr on 2006-03-23
I think you can edit the /etc/apt/source.list for this. In the first line you'll find the cd/dvd part (uncomment it #) .... just add an entry with your path to the dvd-copy and give it a try!

---

