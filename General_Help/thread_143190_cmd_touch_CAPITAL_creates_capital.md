---
title: "cmd touch CAPITAL creates capital"
date: 2006-03-12
forum: General Help
---

### Post by davidhong on 2006-03-12
```
% touch CAP
% ls
cap
```
When it should be capitalised.

This in gnome-terminal. Anyone know how to fix this?

---

### Post by nanotube on 2006-03-12
works as it should for me.... did this start happening recently, or is this the way the system behaved since install?

---

### Post by davidhong on 2006-03-12
This problem appears to be a bug: [http://lists.debian.org/debian-kernel/2005/10/msg01053.html](http://lists.debian.org/debian-kernel/2005/10/msg01053.html)

---

### Post by dcstar on 2006-03-12
[QUOTE=davidhong]This problem appears to be a bug: [http://lists.debian.org/debian-kernel/2005/10/msg01053.html](http://lists.debian.org/debian-kernel/2005/10/msg01053.html)[/QUOTE]
It is only a "bug" if it did it on a filesystem that is case sensitive, and since it is supposed to behave that way on FAT filesystems, it is working as designed for compatibility with this sort of filesystem.

The touch command works fine on my system, on my EXT3 filesystem is handles upper and lower case, on a FAT filesystem it is case insensitive.

If you have Linux installed on a non-case sensitive filesystem (like FAT/FAT32), then annoying things like this will arise.

---

### Post by davidhong on 2006-03-12
Yes, however, the link does not clearly state whether it is to behave as case insensitive on FAT filesystem using utf8. I was wondering if there is a fix to enforce case sensitivity.

One interesting note though: when I view the file I create using "touch A" in linux, its a. but in windows it shows as A.

---

