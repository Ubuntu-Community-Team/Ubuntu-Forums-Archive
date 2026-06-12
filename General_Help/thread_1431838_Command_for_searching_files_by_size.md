---
title: "Command for searching files by size"
date: 2010-03-17
forum: General Help
---

### Post by satish_j on 2010-03-17
Command to find files in Ubuntu by size range???
say for ex:>25MB and <100 MB..

---

### Post by nothingspecial on 2010-03-17
You could use find with the -size argument.

From the directory you are searching from
```

find ./ -type f -size +25M -size -100M
```

---

### Post by satish_j on 2010-03-17
> **nothingspecial said:**
> 
```

find ./ -type f -size +25M -size -100M
```

What does ./ in above command stand for??

---

### Post by nothingspecial on 2010-03-17
It means "from here".

. is linux short hand for the current directory, you dont actually need the /

You have to tell find where to look so if you wanted to search your music directory and you are in your home directory either
```

cd ~/music
find ./ -type f -size +25M -size -100M
```

or ```


find ~/music/ -type f -size +25M -size -100M
```

Because you didn`t say where you wanted to look I put from the directory you want to look in and used ./

---

### Post by nothingspecial on 2010-03-17
2 other things that might be useful

by default find will search all directories within the directory you tell it to look in (unless you specify otherwise)

If you want to search the entire file system, specify / and use sudo.

---

### Post by satish_j on 2010-03-17
Does it mean that below command will search in current directory and all sub-directories??
```

find ./ -type f -size +25M -size -100M

```
whereas,foll command will do search only on current directory and not its sub-directories??
```

find . -type f -size +25M -size -100M

```

---

### Post by ratcheer on 2010-03-17
No, both forms will start at the current directory and search all subdirectories.

Tim

---

### Post by satish_j on 2010-03-17
> **nothingspecial said:**
> 2 other things that might be useful

by default find will search all directories within the directory you tell it to look in (unless you specify otherwise)

If you want to search the entire file system, specify / and use sudo.

Why do i need to use 'sudo' for searching entire filesystem??Does an admin user does not have Read rights by default on the files owned by root??

---

### Post by nothingspecial on 2010-03-17
> **satish_j said:**
> Why do i need to use 'sudo' for searching entire filesystem??Does an admin user does not have Read rights by default on the files owned by root??

```
find: ‘./proc/2/task/2/fd’: Permission denied
find: ‘./proc/2/task/2/fdinfo’: Permission denied
find: ‘./proc/2/fd’: Permission denied
find: ‘./proc/2/fdinfo’: Permission denied
find: ‘./proc/3/task/3/fd’: Permission denied
find: ‘./proc/3/task/3/fdinfo’: Permission denied
find: ‘./proc/3/fd’: Permission denied
find: ‘./proc/3/fdinfo’: Permission denied
find: ‘./proc/4/task/4/fd’: Permission denied
find: ‘./proc/4/task/4/fdinfo’: Permission denied
find: ‘./proc/4/fd’: Permission denied
find: ‘./proc/4/fdinfo’: Permission denied
find: ‘./proc/5/task/5/fd’: Permission denied
find: ‘./proc/5/task/5/fdinfo’: Permission denied
find: ‘./proc/5/fd’: Permission denied
find: ‘./proc/5/fdinfo’: Permission denied
find: ‘./proc/6/task/6/fd’: Permission denied
find: ‘./proc/6/task/6/fdinfo’: Permission denied
find: ‘./proc/6/fd’: Permission denied
find: ‘./proc/6/fdinfo’: Permission denied
find: ‘./proc/7/task/7/fd’: Permission denied
find: ‘./proc/7/task/7/fdinfo’: Permission denied
find: ‘./proc/7/fd’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
```

etc, etc, etc

---

### Post by falconindy on 2010-03-17
> **nothingspecial said:**
> ```
find: ‘./proc/2/task/2/fd’: Permission denied
find: ‘./proc/2/task/2/fdinfo’: Permission denied
find: ‘./proc/2/fd’: Permission denied
find: ‘./proc/2/fdinfo’: Permission denied
find: ‘./proc/3/task/3/fd’: Permission denied
find: ‘./proc/3/task/3/fdinfo’: Permission denied
find: ‘./proc/3/fd’: Permission denied
find: ‘./proc/3/fdinfo’: Permission denied
find: ‘./proc/4/task/4/fd’: Permission denied
find: ‘./proc/4/task/4/fdinfo’: Permission denied
find: ‘./proc/4/fd’: Permission denied
find: ‘./proc/4/fdinfo’: Permission denied
find: ‘./proc/5/task/5/fd’: Permission denied
find: ‘./proc/5/task/5/fdinfo’: Permission denied
find: ‘./proc/5/fd’: Permission denied
find: ‘./proc/5/fdinfo’: Permission denied
find: ‘./proc/6/task/6/fd’: Permission denied
find: ‘./proc/6/task/6/fdinfo’: Permission denied
find: ‘./proc/6/fd’: Permission denied
find: ‘./proc/6/fdinfo’: Permission denied
find: ‘./proc/7/task/7/fd’: Permission denied
find: ‘./proc/7/task/7/fdinfo’: Permission denied
find: ‘./proc/7/fd’: Permission denied
find: ‘./proc/7/fdinfo’: Permission denied
```

etc, etc, etc

These are files on a psuedo filesystem that exists only in RAM. You'd get a negligible difference in results by just doing:

```
find . -type f -size +25M -size -100M 2>/dev/null
```

Bonus: you don't need to use sudo.

---

### Post by satish_j on 2010-03-27
How to search files in a particular folder that contains the term 'U2' anywhere???Is the foll sntax OK?
```

find /media/SATISH/important\ folder/ -type f "%U2%"

```
Got it: '-name' was missing...solved

---

### Post by nothingspecial on 2010-03-27
-iname if you don`t know the case ie u2 or U2

---

