---
title: "Delete multiple files"
date: 2009-11-17
forum: General Help
---

### Post by Philip Gray on 2009-11-17
Hi in Linux how do you delete all the files in a folder in one go? In Windows you enter del *.*.

Regards
Philip

---

### Post by blur xc on 2009-11-17
```
rm *
```

BM

---

### Post by hal8000 on 2009-11-17
You have to be extremely careful here as if you are in the wrong directory you can wipe the entire filesystem.

You change into the folder
e.g cd /home/tux/pictures

or shortcut  cd ~/pictures

then
 rm  *

the * will delete all the files in the current folder.

If the folder itself contains folders

then
  rm -r *
will do the job for you.

To prevent being asked if you want to delete a particular file
use the "f" option
e.g.
rm -rf *

deletes all files and folders at present location however be extremely careful with this command as if youre in the wrong directory you can wipe the entire file system

---

### Post by SuperSonic4 on 2009-11-17
> **hal8000 said:**
> deletes all files and folders at present location however be extremely careful with this command as if youre in the wrong directory you can wipe the entire file system

Only as root. Data files such as ~/Pictures can be deleted as user (although bear in mind that user docs are more important than root docs - it's easy to reinstall but not to get the music back)

If you want a GUI you can press Ctrl+A to select all and then Shift+Del to bypass the trash

---

### Post by Tickborn on 2009-11-17
Hi,
From a Terminal you can access the folder where the files are located and from within use
> 
rm *
In case you need to eliminate directories and subdirectory
> 
rm -r *targetfolder*
To force to delete without confirming for every folder
> 
rm -rf *targetfolder*
But be careful withthe last one! It is..powerful ;)

Depending onwhere the files are located, you mayneed Super User privilege, obtained by typing 'sudo' in front of the command line

---

### Post by Philip Gray on 2009-11-17
Hi folks thanks for yr quick responses. I really appreciate it.

Regards
Philip

I dislike Windows. If my blue Fiat Palio gave me as many problems as Windows does. it would never leave its' garage

---

