---
title: "Apt-get can hardly install anything!"
date: 2006-04-19
forum: General Help
---

### Post by NodlezFodlez on 2006-04-19
I have Ubuntu, and I was planning on installing "kubuntu-desktop", but when I tried, it says "can't find package kubuntu-desktop"! same thing happens with other things like wifi-radar, ardour-gtk, etc.

Why is this happening, and do you think it has anything to do with the installer saying my CD was corrupt midway through the package install thing?

---

### Post by unbuntu on 2006-04-19
Have you tried installing using synaptic?

---

### Post by Sef on 2006-04-19
> ...do you think it has anything to do with the installer saying my CD was corrupt midway through the package install thing?

Yes, likely it does have.

> Why is this happening....

Sounds like more than your CD was corrupt on install.  A reinstall may be the best way to go, although someone with more expertise could tell you another way.  If you reinstall, I would use another disk if you have one.

---

### Post by NodlezFodlez on 2006-04-19
they aren't in synaptic

maybe its because there aren't powerpc packages for these apps

has anyone succesfully installed ardour on a power pc from apt-get or some similar package thing?

---

### Post by NodlezFodlez on 2006-04-19
I actually by accident solved my problem (or at least helped)

When in synaptic, I accidentally clicked repositories (under settings). I saw that the only one was CD Ubuntu Breezy Badger (binary). Then I added Ubuntu Breezy Badger (binary) and suddenly there were many more packages, including ardour and kubuntu, etc

so... try that

---

### Post by Donnut on 2006-04-19
Also make sure to run sudo apt-get update.  It solves many problems.

---

