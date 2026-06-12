---
title: "Installing current setup to external hard disk"
date: 2011-11-08
forum: General Help
---

### Post by rng on 2011-11-08
I think remastersys is used to create an iso file of the current installation of ubuntu so that it can be used to install the system elsewhere. Is it possible to install the current working setup of ubuntu to an external hard disk (without creating an iso file)?

---

### Post by jerrrys on 2011-11-08
[clonezilla]("http://clonezilla.org/")

---

### Post by rng on 2011-11-08
Thanks.

---

### Post by rng on 2011-11-12
I saw following command at another site. Will it work?

sudo dd if=/dev/sda of=/dev/sdb conv=noerror,sync

---

