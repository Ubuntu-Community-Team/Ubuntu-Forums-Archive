---
title: "How to access sub-pages of a man page"
date: 2010-08-28
forum: General Help
---

### Post by paracaudex on 2010-08-28
If I type

```
man perl
```

on the command line, I get the man page for perl, which lists all of the sections into which the perl man pages have been split. How do I access one of these sections? For instance, the first section is perlintro, but if I type

```
man perlintro
```

I get an error saying there is no such manual entry. How do I access these parts of the manual?

Thanks!

---

### Post by AlphaLexman on 2010-08-28
See:
[http://perldoc.perl.org/perlintro.html](http://perldoc.perl.org/perlintro.html)

---

### Post by paracaudex on 2010-08-28
Thanks! The article mentioned perldoc, which it turns out I don't have installed.

```
apt-get install perl-doc
```

fixed it. I now have all the perl docs.

---

