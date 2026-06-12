---
title: "how do i remove the windows boot screen after uninstalling WUBI ?"
date: 2009-12-18
forum: General Help
---

### Post by cain071546 on 2009-12-18
i was just wondering if anybody knows

---

### Post by yavoh on 2009-12-18
Find the boot.ini file in the root of the drive on which Windows is installed.  Remove the options you don't want (in this case, Ubuntu/WUBI).  Be VERY VERY VERY VERY careful when editing this!  You can make your system (temporarily) unbootable.

Back up the boot.ini file first, and if you get into trouble, you can always use your Ubuntu LiveCD to restore it.  Good luck!

---

### Post by Cheesemill on 2009-12-18
Google for a Windows app called EasyBCD, this will do what you want.

---

