---
title: "How do I make a folder hidden in Ubuntu?"
date: 2009-09-04
forum: General Help
---

### Post by Ubu4moi on 2009-09-04
How do I hide a folder or file in Ubuntu Ultimate Edition?

---

### Post by absolutezero1287 on 2009-09-04
> **Ubu4moi said:**
> How do I hide a folder or file in Ubuntu Ultimate Edition?

In any version of Linux and most UNIX-like operating systems its as easy as putting a "." before the name of the directory.

i.e. /home/user/.backup is a hidden directory but /home/user/backup isn't

---

### Post by Whiffle on 2009-09-04
Rename it with a "." at the front of the name.  Ex.  ".wine"

---

### Post by themusicalduck on 2009-09-04
Just rename the folder with a . in front of it. Like ".ubuntu" for instance.

---

### Post by Vaphell on 2009-09-04
~ at the end of filename appears to hide too (backup files made by gedit for example)

---

### Post by CatKiller on 2009-09-05
If you want the file to just not appear in Nautilus, and you don't want to change its name, you can create a file in the same directory called **.hidden**. This file will be hidden by default, as above. If you put a list of file/directory names in this file, they too will be hidden by default. It doesn't affect the command-line, and it doesn't work in all file managers, but it does work in Nautilus (Gnome's file manager).

---

### Post by defacto on 2009-09-05
```
echo "InvisibleFolder" > .hidden

```

---

