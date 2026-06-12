---
title: "How to became super user in the graphical environment?"
date: 2010-05-31
forum: General Help
---

### Post by OdracirAlv on 2010-05-31
I would like to know  
 How to became super user in the graphical environment.
 

 I mean, not in the terminal (using sudo).
 

 Something I want to move files into protected areas and I just get “permission denied”.
 I would like to be able to have a sudo equivalent in the graphical environment.
 

 Thanks in advance

---

### Post by philinux on 2010-05-31
From a terminal
```
gksu nautilus
```

Here be dragons, be careful using this. And if you delete anything it ends up in roots trash not the users trash.

Another way is to install the nautilus-gksu package which then lets you right click on a folder and gives an option to open as administrator. This is what I use.

---

