---
title: "create file with group"
date: 2009-08-09
forum: General Help
---

### Post by dread22 on 2009-08-09
Hi I'm wondering is there a way to change the group under which all new files are created. Similar to umask, instead of modifying permission before write can you change group rather than having to go through with chgrp afterwards because it gets annoying for having to run it on large directories.


Instead of 
$ touch README
$ ls
-rw-rw-r-- 1 root root 1000 2009-01-01 00:01 README
$ chgrp root:special README
$ ls
-rw-rw-r-- 1 root special 1000 2009-01-01 00:01 README

Something like
$ XXX root:special
$ touch README
$ ls
-rw-rw-r-- 1 root special 1000 2009-01-01 00:01 README

Cheers

---

### Post by CatKiller on 2009-08-09
I think the behaviour you want happens if you have setgid on the parent directory.

---

