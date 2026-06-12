---
title: "Make a list"
date: 2011-02-25
forum: General Help
---

### Post by Andreas1982 on 2011-02-25
Is it possible to make a script that makes a tree of all folders and subfolders and outputs it to either a .txt file or .pdf?

All folders except from one shall list 2 levels.
The except folder all the way.

---

### Post by seawolf167 on 2011-02-25
Easiest way would probably be to use ls, though you can get much more complicated if you want to only list specific parts or sort by folder/subfolder etc.

ls man page

```
man ls
```then using a command like

```
ls -R > ~/Desktop/my-file-list.txt
```

---

### Post by hwttdz on 2011-02-25
To list list directories up to two levels deep in the current directory: 
find . -maxdepth 2 -type d
(i.e. find all type directory up to a maximum depth of 2), I think it's probably easiest to split it into two different find commands. The other being something like
find specialdirectory -type d
And you can pipe (>) both to a text file and do what you will. 

I also usually feed find the -xdev flag to keep it from wandering off onto other filesystems (I'm kind of surprised it's not the default option).

---

### Post by oldos2er on 2011-02-25
For fun I ran **tree /* > tree.txt** but that makes no exceptions, obviously.

---

