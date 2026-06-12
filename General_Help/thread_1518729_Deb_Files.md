---
title: "Deb Files"
date: 2010-06-27
forum: General Help
---

### Post by Oolongtea on 2010-06-27
I figure since I've been using Xubuntu for little over a year I should learn how to make a deb file. Anyone know how?

---

### Post by marshmallow1304 on 2010-06-27
The procedure differs based on different standards among distributions.
For example: [Ubuntu Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide"), [Debian Maintainers' Guide]("http://www.debian.org/doc/maint-guide/")

Of course, if you just want to make informal debs for your own personal use, you can use
```
checkinstall
```
in place of
```
make install
```
after compiling.

---

