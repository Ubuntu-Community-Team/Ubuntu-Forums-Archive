---
title: "Sync Home Directory"
date: 2009-10-08
forum: General Help
---

### Post by Jason Cook on 2009-10-08
Does anyone know of a way to sync my home directory with two other network locations?

---

### Post by StuartN on 2009-10-08
> **Jason Cook said:**
> Does anyone know of a way to sync my home directory with two other network locations?

Unison [http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/) or just store your home directory on a network location (or symlink the important subdirectories).

---

### Post by Peter09 on 2009-10-08
Also **conduit** is a similar application

---

### Post by slice16 on 2009-10-08
[http://getdropbox.com](http://getdropbox.com) is also a good tool :)

---

### Post by Jason Cook on 2009-10-08
> **StuartN said:**
> store your home directory on a network location (or symlink the important subdirectories).

I am using a net book so doing that would be impossible. You suggesting that made me wonder if thier was a way to mount a network drive on start up?

---

### Post by Peter09 on 2009-10-08
You can mount a network drive using fstab (look it up) but you would not want to do that anywhere except on a LAN.

---

