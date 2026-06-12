---
title: "Can't run any executable files"
date: 2011-03-06
forum: General Help
---

### Post by aropop on 2011-03-06
Hi,
I got some strange stuff going on, recently i installed ubuntu with wubi, dual boot.
But on windows i cleaned my C and i noticed i cleaned up my update for ubuntu aswell (on dual boot screen you could there were versions of ubuntu).
When i launched ubuntu it was like the first time i opened ubuntu (all standard preferences and stuf) and when i tried to execute a piece of software (on another hard disk then ubuntu) it would load. All other software then the preinstalled ones wouldn't load.

I can see the files in the file browser and in the terminal, i can chmod them but when i try to load em i get  "no such file or directory"

example
```
arno@ubuntu:/media/Linux/gridwars$ ls -l
total 632
-rw------- 1 arno arno  95288 2006-02-17 21:25 bass.dll
-rw------- 1 arno arno   3302 2006-03-09 13:49 Config.txt
drwx------ 6 arno arno   4096 2006-03-14 09:27 gfx
-rwxr-xr-x 1 arno arno 529332 2006-03-16 03:25 grid
drwx------ 2 arno arno   4096 2006-03-14 09:27 music
drwx------ 2 arno arno   4096 2006-03-14 09:27 sounds
arno@ubuntu:/media/Linux/gridwars$ ./grid
bash: ./grid: No such file or directory
```
You can see that the file is there, but when i load it, it says it doesn't
Please help?

---

