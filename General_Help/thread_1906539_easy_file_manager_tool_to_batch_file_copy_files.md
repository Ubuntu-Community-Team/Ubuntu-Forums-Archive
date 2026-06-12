---
title: "easy file manager tool to batch file copy files"
date: 2012-01-09
forum: General Help
---

### Post by linux_tech on 2012-01-09
issue: I used photorec tool to recover files from a drive. It recovered everything to a bunch of different sub-folders, alot of files, (approx 250k) I want to search all of those subfolders at once and copy all jpg, to a seperate folder The computer is slow on cpu and memory so am look for an easy, quick as possible, low resource tool to pull the files out by type, ie. *.jpg, *.exe, from all the subdirectories and cp them to a new folder.
Any suggestions welcome.  thanks

---

### Post by bluexrider on 2012-01-09
GPRename, gwenrename or Krename

available in the repositories

---

### Post by gsgleason on 2012-01-09
```
shopt -s globstar  
cp **/*.jpg **/*.exe /path/to/wherever
```

If you want to do case insensitive (for .jpg, .JPG, etc), do this first:
```
shopt -s nocaseglob
```

---

### Post by linux_tech on 2012-01-09
The rename tool will rename existing files but will it also copy
the file to a separate directory ?

---

### Post by linux_tech on 2012-01-09
Thanks for the help, the files are copying over now.

---

### Post by bluexrider on 2012-01-09
Good deal. Another problem
(SOLVED)

---

