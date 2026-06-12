---
title: "Command line permissions"
date: 2011-11-28
forum: General Help
---

### Post by OpenSage on 2011-11-28
I am wondering if there is a command that will let me change the permissions on every file and directory that are located within a directory.  For example if I wanted to change the permissions to 777 for every file and directory in .thunderbird directory and everything it contains.  I don't want to have to change the permissions on say 50 items separately.

```
opensage@opensageUE:~/PermTest01$ chmod 775 SubDir01
opensage@opensageUE:~/PermTest01$ ls -l
total 8
drwxrwxr-x 2 opensage opensage 4096 2011-11-28 16:38 SubDir01
drwxr-xr-x 2 opensage opensage 4096 2011-11-28 16:39 SubDir02
opensage@opensageUE:~/PermTest01$ ls -l SubDir01
total 0
-rw-r--r-- 1 opensage opensage 0 2011-11-28 16:30 file01
-rw-r--r-- 1 opensage opensage 0 2011-11-28 16:30 file02
-rw-r--r-- 1 opensage opensage 0 2011-11-28 16:30 file03
-rw-r--r-- 1 opensage opensage 0 2011-11-28 16:30 file04
```

In the above code I would like a command to change all of the permissions for everything contained in SubDir01 .... I am sure there must be a code for that, I just don't know what it is.  :lol:

---

### Post by Habitual on 2011-11-28
> **OpenSage said:**
> ...For example if I wanted to change the permissions to 777 for every file and directory in .thunderbird directory and everything it contains.

Terminal > 
```
find `pwd` .thunderbird/ -type f -exec chmod 777 {} \;
```

or 
```
find .thunderbird/ -type f -exec chmod 777 {} \;
```

or
```
chmod 777 .thunderbird/* -R
```

or
...

---

### Post by OpenSage on 2011-11-28
Most excellent Habitual!!!!!  Worked like a charm.  Thank you very much.  the results are below.

```
opensage@opensageUE:~/PermTest01$ find SubDir01/ -type f -exec chmod 775 {} \;
opensage@opensageUE:~/PermTest01$ ls -l SubDir01
total 0
-rwxrwxr-x 1 opensage opensage 0 2011-11-28 16:30 file01
-rwxrwxr-x 1 opensage opensage 0 2011-11-28 16:30 file02
-rwxrwxr-x 1 opensage opensage 0 2011-11-28 16:30 file03
-rwxrwxr-x 1 opensage opensage 0 2011-11-28 16:30 file04
```

---

### Post by Habitual on 2011-11-28
woo hoo!

Glad it worked out.

---

