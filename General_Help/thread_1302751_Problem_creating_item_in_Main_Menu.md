---
title: "Problem creating item in Main Menu"
date: 2009-10-27
forum: General Help
---

### Post by Cygoku on 2009-10-27
There is a folder in my home folder called wbfs, in this folder there is a executable that need root access to work properly.  

In a terminal if I type 

sudo ./wbfs/wbfs

it will ask me for password and it will launch just fine.  If I type the same in the Command: field of the item properties (Launcher Properties), well nothing happen.  I also tried 

sudo ./home/cygoku/wbfs/wbfs

still wihout any luck.  

Cygoku

---

### Post by dcstar on 2009-10-27
> **Cygoku said:**
> There is a folder in my home folder called wbfs, in this folder there is a executable that need root access to work properly.  

In a terminal if I type 

sudo ./wbfs/wbfs

it will ask me for password and it will launch just fine.  If I type the same in the Command: field of the item properties (Launcher Properties), well nothing happen.  I also tried 

sudo ./home/cygoku/wbfs/wbfs

still wihout any luck.  

Cygoku

```
man gksudo
```

---

