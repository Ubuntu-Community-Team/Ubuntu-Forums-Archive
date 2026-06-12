---
title: "Running fsck from my Ubuntu installation"
date: 2009-11-22
forum: General Help
---

### Post by jeb800e on 2009-11-22
If there a way I can run fsck straight from my Ubuntu installation without using a LiveCD? Maybe there is a code I can put in using the "Magic SysRq Key" that will allow me to do it without screwing up my filesystem and/or hard drive?

---

### Post by fluffman86 on 2009-11-22
sudo touch /forcefsck

then reboot to force a fsck on the next boot.

---

### Post by jeb800e on 2009-11-22
Is this the only way? Thanks, by the way!

---

