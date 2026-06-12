---
title: "Extracting files and their sub-directories?"
date: 2011-12-04
forum: General Help
---

### Post by Spyderkid on 2011-12-04
I'm making a Script which you can run to install icon themes...

However how do I extract a file, (for Example test.zip) and then any compressed files inside that? (so test-sub.tar (which is inside test.zip)

I know how to do the rest :D


*Thanks!*

---

### Post by Spyderkid on 2011-12-05
bump?

---

### Post by Lars Noodén on 2011-12-05
The common way to do it is to [tar](http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html) and [gzip](http://manpages.ubuntu.com/manpages/precise/en/man1/gzip.1.html).

```

tar zcf *sometarball.tar.gz* */path/to/directory*

```

You can also use **bzip2** instead of **gzip** by substituting j for z above.

[http://www.catb.org/jargon/html/T/tarball.html](http://www.catb.org/jargon/html/T/tarball.html)

---

### Post by Spyderkid on 2011-12-05
thaaanks :D

---

