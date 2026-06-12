---
title: "Users and permissions"
date: 2010-03-07
forum: General Help
---

### Post by sloshymon on 2010-03-07
I am experimenting with users and there permissions ( I am a newer user) i have tried chown. and tried changing groups. still no luck, will anyone help me figure out how to... user1 and user2 have 3 directories d1, d2, d3,  where u1 can read write in d1 and u2 can read write in d2. User2  can not read or write files in d1, and user1 cannot read or write in d2. and only those users can read or write those files??? thanks for any help.

---

### Post by darolu on 2010-03-07
You can read the documentation you need by opening a terminal, and typing:
```
$ man chown
```
Also read:
```
$ man chmod
```

They general syntax for chown is:
```
$ sudo chown <user>:<group> file1 file2 ...
```

Then you can check your changes with:
```
$ ls -l
```

Examples:
1) Create a -dummy- directory and 3 empty files:
```
$ mkdir dummy
$ cd dummy
~/dummy$ touch file1 file2 file3
```
2) Change user to file 1 and 3 to dummy; then group for file 2 and 3 to test:
```
~/dummy$ sudo chown dummy file1 file3
~/dummy$ sudo chown :test file2 file3
```
3) Check results.
```
~/dummy$ ls -l
total 0
-rw-r--r-- 1 dummy user   0 2010-03-07 17:53 file1
-rw-r--r-- 1 user test 0 2010-03-07 17:53 file2
-rw-r--r-- 1 dummy test   0 2010-03-07 17:53 file3
```

---

### Post by sloshymon on 2010-03-07
As i stated in my second sentence, i have been trying that, actually for around 4 hours now.

---

### Post by sloshymon on 2010-03-07
root@ubuntu:/home/test/Desktop/test# chown u1 d1
root@ubuntu:/home/test/Desktop/test# chown u2 d2
root@ubuntu:/home/test/Desktop/test# ls -l
total 16
drwxr-x--- 2 u1   test 4096 2010-03-07 14:21 d1
drwxr-xr-x 2 u2   test 4096 2010-03-07 14:21 d2
drwxr-xr-x 2 test test 4096 2010-03-07 14:21 d3
-rwxr-xr-x 1 test test  476 2010-03-07 14:07 gnome-terminal.desktop
root@ubuntu:/home/test/Desktop/test#

i understand how to change groups

---

### Post by cjhabs on 2010-03-07
> **sloshymon said:**
> I am experimenting with users and there permissions ( I am a newer user) i have tried chown. and tried changing groups. still no luck, will anyone help me figure out how to... user1 and user2 have 3 directories d1, d2, d3,  where u1 can read write in d1 and u2 can read write in d2. User2  can not read or write files in d1, and user1 cannot read or write in d2. and only those users can read or write those files??? thanks for any help.

chown u1 d1
chmod 700 d1
chown u2 d2
chmod 700 d2

or am i misunderstanding your question?

---

### Post by asmoore82 on 2010-03-07
+1

to change group ownership, use `chgrp` -OR- I prefer the longer form of chown...

```
chgrp *<newgroup>*
```
-OR-
```
chown *<newuser>***[COLOR="Red"][SIZE="3"]:[/SIZE][/COLOR]***<newgroup>*
```
^you need a literal colon( : ) in there

---

