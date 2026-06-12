---
title: "Using chmod for entire directories"
date: 2006-02-28
forum: General Help
---

### Post by remick182 on 2006-02-28
I'm wondering if there is a way to chmod all files and subdirectories inside a folder to add write ability.  I read the man page as well as did a search on the net, but haven't been able to understand if I can knock out a whole folder at once or not.

I've copied the installation of Baldur's Gate 2 from my winxp partition to Ubuntu, but all files and folders are locked from writing, and I believe it is causing the game to not load.  Any help would be greatly appreciated.  Thanks.

---

### Post by kaamos on 2006-02-28
```
chmod +w /path/to/folder **-R**
```
Stands for recursive.

---

### Post by towsonu2003 on 2006-02-28
[QUOTE=remick182]all files and subdirectories inside a folder to add write ability.  [/QUOTE]
chmod -R u+w /path/to/folder

edit: slow typing
note: +w [kaamos] -> write permissions for everyone ||  u+w [towsonu] -> write privilege for you only

---

### Post by remick182 on 2006-03-01
Thanks.  That helps alot.;)

---

