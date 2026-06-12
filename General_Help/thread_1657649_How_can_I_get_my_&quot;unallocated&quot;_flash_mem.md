---
title: "How can I get my &quot;unallocated&quot; flash memory to function?"
date: 2011-01-01
forum: General Help
---

### Post by zozza on 2011-01-01
I have a flash memory stick which according to GParted is "unallocated".

As such it does not appear in File Browser or Gnome terminal. 

How can I get it to function?  I don't mind formatting it but it is not showing.  GParted will not let me change anything.

---

### Post by coffeecat on 2011-01-01
> **zozza said:**
>   GParted will not let me change anything.

Have you tried highlighting the unallocated space and then Partition > New?

If that is not working, in Gparted, Device > Create Partition Table and create a new ms-dos partition table. Then as above, highlight the unallocated space and use the Partition menu or the new partition button, the leftmost on the toolbar.

---

### Post by coffeecat on 2011-01-01
EDIT: inadvertent duplicate. Browser problem.

---

