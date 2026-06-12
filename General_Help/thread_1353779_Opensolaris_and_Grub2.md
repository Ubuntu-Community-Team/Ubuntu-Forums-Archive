---
title: "Opensolaris and Grub2"
date: 2009-12-13
forum: General Help
---

### Post by deancasino on 2009-12-13
I have installed Opensolaris on an additional hard drive, but it does not show in the boot menu. How do I achieve this? 

I have also noticed Ubuntu no longer recognises the hard drive now Opensolaris is on it.

---

### Post by Leppie on 2009-12-13
I believe OpenSolaris now uses grub2 as well.
Try to do update grub:
```
$sudo update-grub
```
Or as some others prefer:
```
$sudo grub-mkconfig
```

What filesystem did you install OpenSolaris on? You may have to install the tools for that filesystem first.

---

