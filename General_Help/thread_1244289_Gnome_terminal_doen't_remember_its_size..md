---
title: "Gnome terminal doen't remember its size."
date: 2009-08-19
forum: General Help
---

### Post by yesint on 2009-08-19
Dear All,
Is it possible to force gnome terminal to remember its size on the next start? Standard 80x24 is too small for me, so each my session starts from resizing the terminal. When I close it the size is lost and 80x24 appears again. There is no option for this anywhere, so I wonder if it is possible...

---

### Post by DaithiF on 2009-08-19
Hi,
yes, you can pass the --geometry parameter to gnome-terminal on startup to specify the size you want.  You may want to create a launcher for this.

---

### Post by yesint on 2009-08-19
> **DaithiF said:**
> Hi,
yes, you can pass the --geometry parameter to gnome-terminal on startup to specify the size you want.  You may want to create a launcher for this.

Thanks, this works. However, this is not exactly what I want. I just wonder why there is no such option to remember the size. The terminal in KDE remember its size nicely...

---

