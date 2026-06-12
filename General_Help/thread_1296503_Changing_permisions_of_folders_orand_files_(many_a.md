---
title: "Changing permisions of folders or/and files (many at once)"
date: 2009-10-20
forum: General Help
---

### Post by WestCity on 2009-10-20
Hi,

I know only 2 ways to change permisions of folders/files: 1. "sudo chmod 777 <folder/file>" 2. "sudo nautilus" -> properties of folder/file -> permisions blah blah...
In both ways possible to change permision of one folder/file at once. The problems is...I need to change permision  from "root" to "my username" or to "all users" (whatever...) of 3 folders, witch including hundreds of folders and files inside...

Any suggestions? :)

---

### Post by t0p on 2009-10-20
> **WestCity said:**
> Hi,

I know only 2 ways to change permisions of folders/files: 1. "sudo chmod 777 <folder/file>" 2. "sudo nautilus" -> properties of folder/file -> permisions blah blah...
In both ways possible to change permision of one folder/file at once. The problems is...I need to change permision  from "root" to "my username" or to "all users" (whatever...) of 3 folders, witch including hundreds of folders and files inside...

Any suggestions? :)

```
sudo chown username /home/username/directory/*
```will change file and directory ownership of all files and subdirectories in ~/directory to username.

---

### Post by WestCity on 2009-10-24
It's not working for me. Let's say, I have 3 folders named A, B and C in /var/www/. If I do "sudo chown username /var/www/*", it changes permisions ONLY for A, B and C, but all subfolders and files in A, B and C will still be under root control. Any ideas?

---

### Post by sisco311 on 2009-10-24
```
chown -R username /path/to/dir
```

-R, --recursive =  operate on files and directories recursively

---

### Post by WestCity on 2009-10-24
Thank you very much! Problem solved. :)

---

### Post by sisco311 on 2009-10-24
> **WestCity said:**
> Thank you very much! Problem solved. :)

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

