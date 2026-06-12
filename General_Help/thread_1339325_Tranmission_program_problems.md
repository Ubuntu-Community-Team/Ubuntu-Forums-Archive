---
title: "Tranmission program problems"
date: 2009-11-27
forum: General Help
---

### Post by jessiebrownjr on 2009-11-27
I manually upgraded Tranmission by adding the PPAs etc. The problem that occurred is Ubuntu did one of the normal system upgrades, but during this system upgrade, it removed transmission. Now when I try to install it via synaptic, it tells me this..

transmission:
```
 Depends: transmission-cli but it is not going to be installed
 Depends: transmission-gtk but it is not going to be installed
```Now, if I try to install transmission-gtk, I get
```
transmission-gtk:
 Depends: libevent-1.4-2 (>=1.4.11-stable) but it is not installable


```Now what do I do? I posted this in another section but got no responses. Really need to get this fixed.

---

### Post by jessiebrownjr on 2009-11-27
Marking as solved, a simple google search for that library gave me a .deb package, which fixed my problem... just wish I knew what caused it in the first place!

---

