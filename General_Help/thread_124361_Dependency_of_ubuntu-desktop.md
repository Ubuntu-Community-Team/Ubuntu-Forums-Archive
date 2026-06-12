---
title: "Dependency of ubuntu-desktop"
date: 2006-02-01
forum: General Help
---

### Post by pbb on 2006-02-01
Hi, I tried uninstalling xsane, the scanner program. But then I saw that ubuntu-desktop is actually dependend on xsane? :confused:

Is it true that I cannot remove xsane without messing up my total Ubuntu installation? I would like to do a clean install of xsane, because I seemingly messed it up trying to upgrade to a newer version...

Thanks, Peter

---

### Post by engla on 2006-02-01
This is the package ubuntu-desktop's description:
"The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system)."

This means what it says. ubuntu-desktop desktop doesn't provide anything in itself

---

### Post by Irony on 2006-02-01
I uninstalled xsane (and thus ubuntu desktop) ages ago because xsane was stopping gimp opening - it hasn't affected anything.

---

### Post by pbb on 2006-02-01
Thanks... Why do they name such a minor package like that? Judging by the name, I would think I would remove my complete GUI when uninstalling ubuntu-desktop!
Anyway, I did it, and reinstalled the original supplied sane. Sadly, I did not solve my problem, my scanner is not recognized anymore (not that it ever worked properly with sane...)

---

### Post by lamego on 2006-02-01
It is not such a "minor package", it is a meta package which basicaly contains a list of dependencies which allow you to install the "minimal" ubuntu desktop with a single package name. 
Installing ubuntu-desktop will get you all the correct packages, removing one of them will "uninstall" it.

---

