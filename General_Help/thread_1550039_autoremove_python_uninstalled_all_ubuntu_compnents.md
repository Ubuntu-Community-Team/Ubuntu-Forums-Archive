---
title: "autoremove python: uninstalled all ubuntu compnents"
date: 2010-08-10
forum: General Help
---

### Post by magnetpest2k7 on 2010-08-10
Hello all,

I gave apt-get autoremove python which removed all the installed components in ubuntu now ubuntu does not boot into graphical mode I am just having the terminal to work on. Is there a way I can restore.

Thanks
Vineeth

---

### Post by endotherm on 2010-08-10
well, try this, though no gaurentees:
```
sudo apt-get install ubuntu-desktop
```
hopefully that will replace everything. 

never uninstall python.

---

### Post by Darkness Des on 2010-08-10
Just about everything uses Python. If you really feel the need to uninstall some core binaries, you could survive without Perl, and possibly Ruby.

---

