---
title: "Flashdrive Problem"
date: 2011-10-27
forum: General Help
---

### Post by anonite on 2011-10-27
Hi, Any flash drive I use through Ubuntu I will add and delete files BUT it will not actually delete the files. They move to the trash but are still there just hidden or something. The files are still there when I boot up with Windows. Any help would really be appreciated.

---

### Post by fdrake on 2011-10-28
they are in the .Trash folder. (.)Dotted named-folders are always hidden , to see them and their files use "Ctrl"+"H" then delete the file. Double check with the free space.

---

### Post by anonite on 2011-10-28
It didn't work 

Name: Games
Type: folder (inode/directory)
Contents: Nothing
Location: /media/3639-3064
Volume: 2.0 GB Filesystem
Free Space: 54.3 MB    <<< but it says "nothing"

---

### Post by fdrake on 2011-10-28
open the terminal (menubar>applications>accessories) and type:
```

gksudo nautilus /media/

```

---

### Post by dfarrell07 on 2011-10-28
A graphical way is to just open your trash and clear it before removing the drive.

---

### Post by anonite on 2011-10-28
> **fdrake said:**
> open the terminal (menubar>applications>accessories) and type:
```

gksudo nautilus /media/

```

I right clicked and unmounted it. Works now. I'm gonna try this with another FD right now to make sure. thanks for the guidance you guys.

---

### Post by anonite on 2011-10-28
> **dfarrell07 said:**
> A graphical way is to just open your trash and clear it before removing the drive.

Had to do this with my kingston. Thank you so much :popcorn:

---

