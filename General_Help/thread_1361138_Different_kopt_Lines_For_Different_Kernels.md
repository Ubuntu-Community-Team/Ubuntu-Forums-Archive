---
title: "Different kopt Lines For Different Kernels?"
date: 2009-12-21
forum: General Help
---

### Post by klausner on 2009-12-21
Is it possible to have different kopt lines, with different options, for different kernels in grub's menu.lst file? I've tried following the syntax included in the comments, but every time I run *update-grub*, it deletes all kopt lines after the first.

---

### Post by klausner on 2009-12-26
Bump.

---

### Post by klausner on 2010-01-23
Bump

---

### Post by flabdablet on 2010-01-23
If you don't want update-grub to mess with the options for your installed kernels, just move the menu entries it has generated for them outside the ### BEGIN AUTOMAGIC... and ### END AUTOMAGIC... lines.

The # kopt= line is used by update-grub, not by grub itself, and as you've found, update-grub only wants one of them. You can do a certain amount of customization using the lines provided for doing stuff with recovery kernels etc. but anything more complicated than that is best done by hand on the menu entries themselves.

---

