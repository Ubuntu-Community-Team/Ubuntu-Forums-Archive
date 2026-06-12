---
title: "Karmic Kernel Updates"
date: 2010-12-01
forum: General Help
---

### Post by carn1x on 2010-12-01
Ok so I guess this is possibly more a question regarding the life cycle of Ubuntu releases and how updates are pushed to them. 

I got Karmic around March 2010, and for the first few months I felt like I was getting kernel updates every couple weeks, as evidenced by my ever growing Grub boot menu. However at some point they just stopped coming, until at some point it just stopped at 2.6.31-22.

Does each major Ubuntu release only ever recieve updates to the kernel within the base of 2.6.31-xxx ? Is it possible to upgrade this further with built in upgrade tools or is that where things get messy for a linux nub?

---

### Post by NCLI on 2010-12-01
> **carn1x said:**
> Ok so I guess this is possibly more a question regarding the life cycle of Ubuntu releases and how updates are pushed to them. 

I got Karmic around March 2010, and for the first few months I felt like I was getting kernel updates every couple weeks, as evidenced by my ever growing Grub boot menu. However at some point they just stopped coming, until at some point it just stopped at 2.6.31-22.
Canonical backports security updates from the newer kernels, and fixes reported bugs. Since the 2.6.31-* series is very stable(old) now, it won't be receiving many updates.

If you want a new kernel, you need to upgrade to a newer version of Ubuntu. You'll have to soon anyway, since [Karmic is reaching EOL]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline").
> Does each major Ubuntu release only ever recieve updates to the kernel within the base of 2.6.31-xxx ? Is it possible to upgrade this further with built in upgrade tools or is that where things get messy for a linux nub?
You can upgrade the kernel yourself, but it's much easier to just upgrade to a newer version of Ubuntu. 

Also, to answer you question: Each version of Ubuntu only receives bugfixes and security updates after it is released, in order to make sure no new bugs are introduced.

---

