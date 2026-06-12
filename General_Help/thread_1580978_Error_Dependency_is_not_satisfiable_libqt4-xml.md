---
title: "Error: Dependency is not satisfiable libqt4-xml"
date: 2010-09-24
forum: General Help
---

### Post by eival on 2010-09-24
[IMG]http://img571.imageshack.us/img571/4446/51035630.png[/IMG]

im using Ubuntu 8.04

---

### Post by teward on 2010-09-24
Simple.  It means that it can't work with libqt4-xml.  You probably need to have an updated version of this package.  If the version doesn't exist in 8.04, then try 10.04 (the OTHER LTS version that's still out there).

Or it means you don't have it, in which case:

```
sudo apt-get install libqt4-xml
```do the above code in terminal and see if it installs something, or if it does nothing.

---

### Post by eival on 2010-09-24
thanks i actually had to enable hardy-backports first, then i was able to install libqt4-xml and the imageshack app

:popcorn:

---

