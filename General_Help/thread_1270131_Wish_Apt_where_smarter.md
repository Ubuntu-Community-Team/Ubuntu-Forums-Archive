---
title: "Wish Apt where smarter"
date: 2009-09-19
forum: General Help
---

### Post by glickboy on 2009-09-19
Does anyone else hate it when you install something, like kmix for example, and it brings in a whole bunch of other packages, and then when you uninstall kmix, those other packages you had install dont get uninstalled with it.  Wish apt could do some smarter tracking and figure out what packages where installed along with a package, and if nothing was installed since that needs those packages, it should assume it is safe to uninstall those packages as well.

---

### Post by scragar on 2009-09-19
That's what aptitude does.

On a side note autoremove will remove orphaned packages, and it can be used with remove at the same time by adding the purge option.
```
apt-get --purge autoremove **package**
```

---

### Post by glickboy on 2009-09-19
Awesome thanks man!

---

