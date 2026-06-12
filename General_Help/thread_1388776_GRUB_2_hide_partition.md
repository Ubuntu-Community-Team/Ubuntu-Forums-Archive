---
title: "GRUB 2 hide partition"
date: 2010-01-23
forum: General Help
---

### Post by Burillo on 2010-01-23
In GRUB 1 there were commands to hide/unhide a partition (e.g. hide (hd0,1)). Is there an equivalent in GRUB 2?

Do not confuse with hiding something from the menu - i want to hide a **partition**.

---

### Post by Burillo on 2010-01-24
In case anyone's interested, the solution is to use a parttool e.g.> parttool (hd0,1) hidden+

---

### Post by sailor.nir on 2011-11-16
Yes, we are interested. Thank you very much!

Here's a description of the typical usage:

[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows)

---

