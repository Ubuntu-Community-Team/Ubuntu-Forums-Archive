---
title: "Compile Ubuntu from the source"
date: 2010-02-07
forum: General Help
---

### Post by fernandoc1 on 2010-02-07
Recently I was trying to use Gentoo, and I was really impressed of how it is faster than Ubuntu in running applications, specially when I build wine and was able to run Oblivion at a reasonable speed.
I would like to know if there is a way to compile Ubuntu from source code, to optimize it to my hardware.

---

### Post by oldos2er on 2010-02-07
If you're wanting to compile a custom kernel, see [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

---

### Post by falconindy on 2010-02-07
Sigh.

[http://funroll-loops.info/](http://funroll-loops.info/)

Simply recompiling everything isn't going to net you any major performance improvements. Sifting through each program's ./configure options and cherry picking out features, functionality, and dependencies that you don't want **will** result in a performance gain.

If you were to emerge everything in Gentoo with your use flags to be the equivalent of how Ubuntu is compiled by the developers, and installed every last package that Ubuntu does, you'd notice extremely similar performance.

---

