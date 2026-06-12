---
title: "move all files from all sub folders to a new folder"
date: 2012-09-24
forum: General Help
---

### Post by sohlinux on 2012-09-24
how can I move all files from all sub folders to a new folder?

folder1 has 1000 files
folder2 has 1000 files 
folder3 has 1000 files
folder4 has 1000 files

move all files to new folder which then has 4000 files

thanks

---

### Post by zombifier25 on 2012-09-24
cd to the directory containing the folders, and
```
mkdir newfolder
cp folder1/* folder2/* folder3/* folder4/* newfolder
```
First command to make a new directory to contain all our files, second one to do the copying.

---

### Post by sohlinux on 2012-09-24
> **zombifier25 said:**
> cd to the directory containing the folders, and
```
mkdir newfolder
cp folder1/* folder2/* folder3/* folder4/* newfolder
```
First command to make a new directory to contain all our files, second one to do the copying.

ok but the folder1234 was just an example, in reality I have 100s of folders all with different names, I want to move (not copy) all the files out of all the folders into a new folder

I dont want to specify the names of all the directories, I just want to recursively move all files from all sub folders into a new folder.

---

### Post by Lars Noodén on 2012-09-24
You could do something with find.  

```

find /some/path/to/folders -type f -exec mv "{}" /path/to/newfolder \;

```

That will get all regular files, not directories, and move them to a single folder.

---

### Post by sohlinux on 2012-09-24
> **Lars Noodén said:**
> You could do something with find.  

```

find /some/path/to/folders -type f -exec mv "{}" /path/to/newfolder \;

```

That will get all regular files, not directories, and move them to a single folder.

thanks ;)

---

