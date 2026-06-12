---
title: "Getting source code instead of binaries"
date: 2011-11-01
forum: General Help
---

### Post by salmontres on 2011-11-01
Hi everyone,

I'd like to download some packages through the standard repository, but I'd like to get the source code rather than the executable (bin) file. Is there a way to do this from the repository page?

---

### Post by WorMzy on 2011-11-01
Sure, it's on the right-hand side.

e.g. on [nautilus' page]("http://packages.ubuntu.com/oneiric/nautilus"), look in the right-hand box which is entitled "Links for nautilus", in the second section down, there's a subheader: "Download Source Package", with links to three files. These are the source packages.

---

### Post by oldos2er on 2011-11-01
Or just use **apt-get source <package>**

---

### Post by mrubnt2 on 2011-11-03
Suppose we need the source code of a function.
How can we find the name of its package?
thanks
regards
Massimo

---

### Post by WorMzy on 2011-11-03
You can use dpkg-query to find out which package a file belongs to.

e.g.

```
dpkg-query -S $(which shutdown)
upstart: /sbin/shutdown
```

---

