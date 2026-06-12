---
title: "Comands bar dissapeared"
date: 2010-02-06
forum: General Help
---

### Post by Sevy123 on 2010-02-06
The bar with applications/places internet connection and all of those just dissapeared...
i am dual-booting with windows xp,xubuntu vers 9.10 
xubuntu works but when i start it oppens firefox and the explorer showing the ntfs partition
help please:(

---

### Post by sisco311 on 2010-02-06
Press Alt+F2 and run:
```
xfce4-panel
```
this should start the panels.

Go to Menu -> Settings -> Session and Startup -> General tab & unselect the *Automatically save session on logout* checkbox.

In the Session tab set the *Restart Style* of the xfce4-panel to *Immediately*.

Open your file browser, press Ctrl+h to list hidden files & remove (or rename) the ~/.cache/sessions directory.

Log out & log back in.

---

### Post by Sevy123 on 2010-02-06
thanks that worked \\:D/

---

