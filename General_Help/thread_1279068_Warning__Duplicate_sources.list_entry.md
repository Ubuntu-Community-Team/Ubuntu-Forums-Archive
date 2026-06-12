---
title: "Warning : Duplicate sources.list entry"
date: 2009-09-30
forum: General Help
---

### Post by Tapas Bose, India on 2009-09-30
Good evening every body.
I got an warning during update by synaptic, and that is
> Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
What does it mean? How to solve it?
Please help..

---

### Post by slakkie on 2009-09-30
It means that line is in there twice. Open /etc/apt/sources.list and remove the duplicate entry.

sudo nano /etc/apt/sources.list

---

