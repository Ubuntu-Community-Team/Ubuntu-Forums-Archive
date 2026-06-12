---
title: "how to hide files"
date: 2010-09-07
forum: General Help
---

### Post by nishant29 on 2010-09-07
hi..

i want to know how to hide files and folders in ubuntu as we have option in windows??

---

### Post by 3Miro on 2010-09-07
The convention is that all files and folders with names starting with . (dot) are considered "hidden". To see them in Nautilus, you have to hit Ctr + H, in terminal you have to list them with "ls -a"

Change the name from myfile to .myfile and the file will be hidden.

---

### Post by nishant29 on 2010-09-07
thank u

---

### Post by bodhi.zazen on 2010-09-07
> **3Miro said:**
> The convention is that all files and folders with names starting with . (dot) are considered "hidden". To see them in Nautilus, you have to hit Ctr + H, in terminal you have to list them with "ls -a"

Change the name from myfile to .myfile and the file will be hidden.

While that works, the Linux way would be to :

1. Give each user a unique log in name and not share accounts.

2. Set your home directory as private (ie use Linux permissions).

```
chmod 770 ~
```

If needed, make the file private as well and / or set a more private umask in .bashrc

This will not help protect files from root, for that you need to use encryption.

---

### Post by 3Miro on 2010-09-07
There is a difference between trying to hide a folder on your computer with private pictures, so that it doesn't show up when someone is walking behind you and hiding a file from someone who has direct access to the machine.

I am covering the "windows" version of hidden files, bodhi.zazen has the more "unix" version. Also, 700 for executables and 600 for regular files are better than 770. Anyone interested can read more about permissions.

---

### Post by The Cog on 2010-09-07
You can also make files hidden (to nautilus but not to the command line) by creating a file called .hidden (which is itself a hidden file because of its name) in the directory in question. Then add the names of the other hidden files in the directory to .hidden, one name per line.

---

### Post by nishant29 on 2010-09-08
but by putting . (dot) eg .xyz shows my folder on screen its not hidden..

---

### Post by WorMzy on 2010-09-08
Refresh. (Ctrl+R|F5)

Putting a tilde (~) at the end of a file name marks it as a backup file, and will also make it hidden.

e.g.
textfile.txt~

---

### Post by mirchichamu on 2010-09-08
> **nishant29 said:**
> but by putting . (dot) eg .xyz shows my folder on screen its not hidden..

When you exit and reopen then it will be hidden. OR you hot ctrl +H then it will go and pressing again ctrl+H will show the hidden files.

---

