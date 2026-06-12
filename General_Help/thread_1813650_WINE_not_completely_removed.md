---
title: "WINE not completely removed"
date: 2011-07-28
forum: General Help
---

### Post by editheraven on 2011-07-28
I tryied installing wine patched for league of legends from the source code
(./configure, make, sudo make install). Wine didn't appeared in the application tab in gnome and then i installed wine from its repo. After uninstalling it i saw that whenever i try to open an exe file, wine still tries to run it, regardless the fact that wine is not present in the application folder. After a search i find that wine libs and files are still there, even after the unistatll. I think they are there because the installation from source files so how do i remove them besides deleting them manually?

---

### Post by CatKiller on 2011-07-28
There's probably a *make uninstall* target with the source that you compiled.

---

