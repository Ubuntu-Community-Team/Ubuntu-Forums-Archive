---
title: "rpm --query --all"
date: 2010-07-26
forum: General Help
---

### Post by mmaru on 2010-07-26
I am a student trying to learn both rpm and dpkg. After installing rpm in my Ubuntu 10.04 desktop copy, I tried the following query with no result:

$rpm --query --all

Is there anything I need to do in addition to installing RMP on Ubuntu and use it?

Your help is very much appreciated.

Maru

---

### Post by Simian Man on 2010-07-26
Installing rpm on Ubuntu won't add any packages to the rpm database.  If you want to learn rpm, you should install an rpm distro.

---

### Post by mmaru on 2010-07-26
Thank you for the quick response. Do you mean that I can't be able to use rpm on Ubuntu to query, install, and uninstall rpm packages? At a mininum, Can I use rpm to query packages that are installed on Ubuntu?

Maru

---

### Post by Simian Man on 2010-07-26
If you install rpm packages with rpm, you can then query them or remove them.  Right now you have no packages in the rpm database so it returns nothing.

It's not a great idea to try this because most rpm packages you'll find will have some dependencies and if you install those with rpm, you may over-write programs and libraries installed by dpkg leading to a broken system.

---

### Post by mmaru on 2010-07-26
Thank you very much for the clear answer.

---

### Post by RiceMonster on 2010-07-26
For the record, you can shorten that command like this:
```
rpm -qa
```

For an rpm distro, I would reccomend Fedora or CentOS. Depends on if you want older and more tested (CentOS) or more flashy and up to date (Fedora).

---

