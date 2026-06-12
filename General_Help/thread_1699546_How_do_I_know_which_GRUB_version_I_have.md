---
title: "How do I know which GRUB version I have?"
date: 2011-03-03
forum: General Help
---

### Post by rva1945 on 2011-03-03
1 or 2?

The GRUB boot menu says GRUB 1.97 beta 4

I tried 

grub --version

but got

The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found

?

---

### Post by stinkeye on 2011-03-03
```
grub-install -v
```
GRUB 2 should display a version number of 1.96 or later. Legacy GRUB is version 0.97.

eg```
glen@MavMusic:~$ grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3
```

---

