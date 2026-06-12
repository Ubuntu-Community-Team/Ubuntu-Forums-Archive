---
title: "/base folder can't be altered?"
date: 2009-07-28
forum: General Help
---

### Post by rabidmedia on 2009-07-28
I swear I'm logged in as administraitor...I'm the only one who uses my computer.
 
I can't seem to be able to add any folders or anything in the file system... only the desktop and home folder...?
 
this really dosen't help much when I need to get prboom or doom 3 to work on it.
 
there is obviously something I don't see happening here...
 
Q: how do I get into the base folder so I can put files in it or add folders?

---

### Post by marshmallow1304 on 2009-07-28
In the terminal, type
```
gksudo nautilus
```
and use the resulting window to manage those files.

But do so with care.

---

### Post by ajgreeny on 2009-07-28
> **rabidmedia said:**
> I swear I'm logged in as administraitor...I'm the only one who uses my computer.
 
I can't seem to be able to add any folders or anything in the file system... only the desktop and home folder...?
 
this really dosen't help much when I need to get prboom or doom 3 to work on it.
 
there is obviously something I don't see happening here...
 
Q: how do I get into the base folder so I can put files in it or add folders?
You may be the only user and as an admin group member have the ability to get admin privileges, but you still can't actually do anything in the filesystem without using **sudo** for cli commands or **gksudo** for any gui programs.  As MM1304 says, proceed with caution, or you could do a lot more harm than good, which is why you can't delete or edit any filesystem files without using the sudo system.  It's a good reminder of the potential damage you could do.

---

### Post by DeMus on 2009-07-28
As my two predecessors stated already: Be very careful. With sudo or gksudo you can destroy everything.
The question is: do you really need to be root? Most of the things on your computer you can do as a normal user, it's very rare you need root privileges.

---

