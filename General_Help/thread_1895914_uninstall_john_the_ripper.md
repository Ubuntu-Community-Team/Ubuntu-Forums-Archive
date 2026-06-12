---
title: "uninstall john the ripper"
date: 2011-12-15
forum: General Help
---

### Post by arunes007 on 2011-12-15
how to uninstall john the ripper using terminal command on ubuntu 10.4?

---

### Post by yetiman64 on 2011-12-15
```
sudo apt-get purge john
```should remove it from the system. You may have left over configuration files hidden in your home directory (look in ~/.config as well) if you want a total cleanout. (Note: CTRL + H in a directory will show hidden files and folders and ~ is a system variable to indicate the users home directory).

---

### Post by arunes007 on 2011-12-18
thanks bro...
cheers...

---

### Post by yetiman64 on 2011-12-18
> **arunes007 said:**
> thanks bro...
cheers...
If all is Ok, can you please mark the thread as solved ? Link #5 in my sig has instructions if needed. Cheers.

---

### Post by BC59 on 2011-12-18
> **yetiman64 said:**
> ```
sudo apt-get purge john
```should remove it from the system. You may have left over configuration files hidden in your home directory (look in ~/.config as well) if you want a total cleanout. (Note: CTRL + H in a directory will show hidden files and folders and ~ is a system variable to indicate the users home directory).

Theoretically the purge command is sufficient to uninstall the config files.

---

### Post by gandaran on 2011-12-18
> **BC59 said:**
> Theoretically the purge command is sufficient to uninstall the config files.
not user files.

---

### Post by yetiman64 on 2011-12-18
> **BC59 said:**
> Theoretically the purge command is sufficient to uninstall the config files.
Sometimes even the purge option will not remove files in the users home directory but only the config files in the system areas. 

I've run into that as a problem quite a few times now, when trying to do a totally fresh install with a program, old settings will sometimes pop up because of the home folder hidden files. This was after using the purge option previously to uninstall.

---

### Post by BC59 on 2011-12-18
> **yetiman64 said:**
> Sometimes even the purge option will not remove files in the users home directory but only the config files in the system areas. 

I've run into that as a problem quite a few times now, when trying to do a totally fresh install with a program, old settings will sometimes pop up because of the home folder hidden files. This was after using the purge option previously to uninstall.

For this reason I comment "theoretically" because I had the problem as you said several times. Finally the difference between "remove" and "purge" is not so definite.

---

### Post by gandaran on 2011-12-18
> Finally the difference between "remove" and "purge" is not so definite
using only the remove command leaves the system configuration files installed, using **remove purge** removes everything from the system but not from home user directory.

---

