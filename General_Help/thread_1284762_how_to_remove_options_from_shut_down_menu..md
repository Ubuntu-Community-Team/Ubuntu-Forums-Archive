---
title: "how to remove options from shut down menu."
date: 2009-10-07
forum: General Help
---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-10-07
As of now the shut down menu has these options

Second username
guest session
lock session
____________
Log out...
suspend
hibernate
restart
shutdown...

I'd like to remove suspend and hibernate from the list, how could i do this?
Thanks in advance.

---

### Post by zeroseven0183 on 2009-10-07
1. press Alt + F2
2. type **gconf-editor**
3. browse to **/apps/gnome-power-manager**
4. uncheck **can_hibernate** and **can_suspend**
 * right-click on the items and **Set as Mandatory**

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-10-09
> **zeroseven0183 said:**
> 1. press Alt + F2
2. type **gconf-editor**
3. browse to **/apps/gnome-power-manager**
4. uncheck **can_hibernate** and **can_suspend**
 * right-click on the items and **Set as Mandatory**
Thanks 07 ;] :popcorn:

---

