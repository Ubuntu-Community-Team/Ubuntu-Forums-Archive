---
title: "How do I install glibc &gt;= 2.6"
date: 2009-08-11
forum: General Help
---

### Post by lixoman100 on 2009-08-11
I need glib >= 2.6.0 installed to compile a piece of software.
How do I install it? If I do apt-get install libglib-dev it offers me glib1.2.

---

### Post by mc4man on 2009-08-11
glib is not something you install, depending on what release of ubuntu you're on many of your core libs are built from a glib source
(( hardy is 2.7, intrepid is 2.8. jaunty 2.9

What you most likely want to do is go (unless your source needs the libglib1.2-dev version

```
 sudo apt-get install libglib2.0-dev
```

you may wish to post what release of ubuntu your using and what your trying to build

---

