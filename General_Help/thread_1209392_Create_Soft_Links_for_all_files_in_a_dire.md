---
title: "Create Soft Links for all files in a dire"
date: 2009-07-10
forum: General Help
---

### Post by vagamente on 2009-07-10
Hi all...

I need to create a symbolic link for EACH AND EVERY file in a dir. How can I?

---

### Post by unutbu on 2009-07-10
```
mkdir shadow
lndir test shadow
```
This will create a directory called "shadow" with symbolic links to every file in the "test" directory.

---

### Post by vagamente on 2009-07-10
Doesn't work...
> From and to directories are identical

---

### Post by unutbu on 2009-07-10
The command works this way:
```

% ls -l test/
total 0
-rw-r--r-- 1 user user 0 2009-07-10 08:12 1.txt
-rw-r--r-- 1 user user 0 2009-07-10 08:12 2.txt
-rw-r--r-- 1 user user 0 2009-07-10 08:12 3.txt

% mkdir shadow
% lndir ~/test shadow

% ls -l shadow/
total 0
lrwxrwxrwx 1 user user 23 2009-07-10 08:13 1.txt -> /home/user/test/1.txt
lrwxrwxrwx 1 user user 23 2009-07-10 08:13 2.txt -> /home/user/test/2.txt
lrwxrwxrwx 1 user user 23 2009-07-10 08:13 3.txt -> /home/user/test/3.txt

```
Please post the commands you used.

---

