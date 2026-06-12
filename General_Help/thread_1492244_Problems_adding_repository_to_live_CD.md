---
title: "Problems adding repository to live CD"
date: 2010-05-24
forum: General Help
---

### Post by Muscovy on 2010-05-24
I tried adding a repository to a live CD, but upon installing the disk, some of the packages had reverted to their Ubuntu version, and the source was no longer added. Booting live was exactly the same, except the repository was still in /etc/apt/sources.list. The CD was Ubuntu 10.04.

Help is highly appreciated, I can't finish this until the software sources are properly added.

---

### Post by Muscovy on 2010-05-25
Investigation is showing the repository is being disabled during boot. All updated packages from the repository, except Plymouth are still installed, but other than that, apt says my modified packages don't exist. Any unique packages are treated normally.

Silly mystified.

---

### Post by Muscovy on 2010-05-28
Bump.

---

### Post by Muscovy on 2010-06-06
Bump.

---

### Post by jerenept on 2010-06-06
> **Muscovy said:**
> I tried adding a repository to a live CD, but upon installing the disk, some of the packages had reverted to their Ubuntu version, and the source was no longer added. Booting live was exactly the same, except the repository was still in /etc/apt/sources.list. The CD was Ubuntu 10.04.

Help is highly appreciated, I can't finish this until the software sources are properly added.

you added a repository to a Live CD?

I'm going to assume that you used Ubuntu Customization Kit or something.
I think you need to enable it in Software sources (as someone probably already said)

System>Administration>Software Sources
Enter password. Go to the tab marked "Other Software" and check the repository that you added.

---

