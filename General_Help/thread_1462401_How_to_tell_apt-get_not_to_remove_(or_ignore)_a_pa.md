---
title: "How to tell apt-get not to remove (or ignore) a package"
date: 2010-04-25
forum: General Help
---

### Post by emamm2008 on 2010-04-25
Hello

There is a package on my system that won't be removed.  How can I tell apt-get not to remove that specific file?

sudo apt-get purge (remove) texlive-lang-cyrillic won't work.

Many thanks

Ed

---

### Post by klemes on 2010-04-25
There is contradiction in what you write.I am not able to tell if you want to **remove** or **hold** the package.If you want to remove it the command you wrote should do it ,if you want to hold it(not be able to be upgraded removed etc):

```
sudo aptitude hold package_name
```

---

### Post by emamm2008 on 2010-04-26
Many thanks.

It does not matter whether it is hold or remove; I just don't want that the package gets in the way of upgrading and installing another package.

What I did was sudo apt-get install trouble_package.  The package didn't install correctly but at least apt-get install is now working for other packages.

Ed

---

