---
title: "GCC / Xampp help/question"
date: 2009-11-08
forum: General Help
---

### Post by lovemylady on 2009-11-08
Xampp Problem with GCC_4.2.0

When I run it I get this error

```
Starte XAMPP fuer Linux 1.7.3-beta2...
/opt/lampp/bin/php: /opt/lampp/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /opt/lampp/lib/libstdc++.so.6)
XAMPP: Starte Apache mit SSL ...
XAMPP: Starte MySQL...
XAMPP: Starte ProFTPD...
XAMPP fuer Linux gestartet.

```

**GCC_4.2.0' not found**

Ehm, does Kubuntu own any version of GCC? If unsure (how can i find it out)
What is GCC?

***Short***: How to fix that problem?

---

### Post by lovemylady on 2009-11-08
Nobody got an Idea?
<.<

---

### Post by SkippoGuangiacomo on 2010-02-28
Late reply but...

Gcc is a Gnu collection compiler (see, [http://gcc.gnu.org/](http://gcc.gnu.org/)). You probably don't have it installed it in your machine. Select it with sinaptic and install it, then it should work

---

