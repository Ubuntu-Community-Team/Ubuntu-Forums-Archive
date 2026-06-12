---
title: "Gparted first or install Ubuntu then Gparted?"
date: 2010-01-08
forum: General Help
---

### Post by tn812 on 2010-01-08
If I want to prepare a harddrive for dual install, which is better (in performance): partition with Gparted first or install ubuntu then gparted to resize and install windows?

---

### Post by Leppie on 2010-01-08
best to install windows first (the installer can create partitions of the size you want), then install ubuntu using the remaining free space.

---

### Post by tom.swartz07 on 2010-01-08
> **tn812 said:**
> If I want to prepare a harddrive for dual install, which is better (in performance): partition with Gparted first or install ubuntu then gparted to resize and install windows?

Ubuntu automatically resizes during the install process, thats what I use 99.9% of the time.

I would suggest if youre dual booting with Windows, Definitely degrag your drive several times first. 2 times minimum.

---

### Post by running_rabbit07 on 2010-01-08
If nothing is installed, you may want to use GParted to lay out the hard drive.

Remember Windows has to be the first Partition and you can only have 4 Primary partitions. Here is how mine looks. It is ugly.

---

### Post by tn812 on 2010-01-08
Why is it that Windows has to be the first partition?  Is it anything to do with startup?

---

### Post by Leppie on 2010-01-08
> **tn812 said:**
> Why is it that Windows has to be the first partition?  Is it anything to do with startup?
this is a myth. windows is a bit more picky than linux however.
use a primary partition to install windows onto (but doesn't have to be the first one). and if you install windows the intelligent way, there's no need to resize ;)

---

