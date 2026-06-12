---
title: "apt-get install question"
date: 2010-10-24
forum: General Help
---

### Post by U_buntu on 2010-10-24
when using apt-get install* package name*. How do you go about uninstalling that package?

---

### Post by howefield on 2010-10-24
apt-get remove packagename

or, if you want rid of configuration files as well as the binary..

apt-get purge packagename

Have a read at man apt-get.

---

### Post by Elfy on 2010-10-24
```
sudo apt-get remove *packagename*
```

```
man apt-get
``` will show you more information

---

### Post by alexandari on 2010-10-24
sudo apt-get remove

or if you are angry

sudo apt-get remove --purge

---

### Post by U_buntu on 2010-10-24
cool, the man pages are weird and confusing. lol Thanks

---

