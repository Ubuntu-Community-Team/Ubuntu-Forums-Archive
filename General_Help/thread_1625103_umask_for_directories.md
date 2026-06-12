---
title: "umask for directories?"
date: 2010-11-18
forum: General Help
---

### Post by XtremeGamer99 on 2010-11-18
I'm just wondering: I know that umask sets the default file permissions for files, however I want to know if there is anyway to set default file permissions for newly created directories.

For example, I want my user to create new directories that anyone can access and modify (777) but I want the new files the user creates to be 755 (read by everyone, written only by user).

Is this possible?

---

### Post by efflandt on 2010-11-18
With typical default umask 022, by default directories have 755 permission (drwxr-xr-x) and files have 644 permission (-rw-r--r--).  The x bit on directories means something different than for files and is necessary to list (ls) or search a directory.

You would not want 755 as a default for files unless the directory only contains executables or scripts.  Otherwise someone could inadvertently "execute" a text or other file with possible unexpected results.

And it is very unwise to give a directory 777 permission, because anybody could create or delete files there.  If you want people to be able to create files, and only write or delete their own files, you should put them in a specific group (like users), chgrp the directory to that group, and chmod 3775 the directory.  Then files they create will take on the group of the directory, and with the typical default umask it would end up looking something like this for **ls -al** from that directory:

```
drwxrwsr-t  3 efflandt users    4096 2010-11-18 21:38 .
drwxr-xr-x 41 efflandt efflandt 4096 2010-11-18 21:24 ..
drwxr-sr-x  2 efflandt users    4096 2010-11-18 21:38 subdir
-rw-r--r--  1 deffland users     230 2010-11-18 21:18 testdd.txt
-rw-r--r--  1 efflandt users     484 2010-11-18 21:24 test.txt
```

But I do not know if or how to set a umask that would automatically give all directories 3775 permission by default, because that might also be unwise, unless intended for a specific directory.

---

