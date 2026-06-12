---
title: "File appears in &quot;ls *&quot; but cannot be accessed - help!"
date: 2010-11-18
forum: General Help
---

### Post by thenickdude on 2010-11-18
Hey everyone,

I'm currently having some major headaches trying to sort out a problem with some of the images I have stored on my host. The files appear in an "ls" listing, but cannot be accessed. As root, I:

```
ls -l 11738*
-rw------- 1 root root 214249 2010-11-18 04:09 117380
-rw------- 1 root root 224524 2010-11-18 04:09 117381
-rw------- 1 root root 170728 2010-11-18 04:09 117382
-rw------- 1 root root  78889 2010-11-18 04:09 117383
-rw------- 1 root root 155639 2010-11-18 04:08 117387
-rw------- 1 root root 663949 2010-11-18 04:08 117389
```
But, also as root:
```
ls 117389
ls: cannot access 117389: No such file or directory
rm 117389
rm: cannot remove `117389': No such file or directory
cat 117389
cat: 117389: No such file or directory
```
Drive is a two-disk RAID0 array mounted like so:
/dev/md1 on /caches type ext2 (rw,noatime)
The folder has 200,000 files in it.

---

### Post by asmoore82 on 2010-11-18
Maybe the filenames have an extra space at the end or something similar.

I would check the output of
```
ls 11738* | cat -A
```

---

### Post by thenickdude on 2010-11-18
Apparently my files have a space on the end of the filename :). Problem solved, thanks :). Now I just have to figure out to how to rename all of them to remove the space.

---

### Post by sisco311 on 2010-11-18
Well, in Ubuntu, you can use the perl based rename command:
```
rename -n 's/ //g' ./*
```
See:
```
man rename
```

---

### Post by thenickdude on 2010-11-18
An "ls" on this directory takes a very, very long time (it's stored on Amazon S3. I'm hoping it will take less than an hour, but who knows), so I'm piping "ls -1" to a file and I'll operate on that afterwards to figure out the rename process. I don't suppose you know how I could work with that file to achieve it instead? :)

---

### Post by sisco311 on 2010-11-18
> **thenickdude said:**
> An "ls" on this directory takes a very, very long time (it's stored on Amazon S3. I'm hoping it will take less than an hour, but who knows), so I'm piping "ls -1" to a file and I'll operate on that afterwards to figure out the rename process. I don't suppose you know how I could work with that file to achieve it instead? :)

If listing the files takes an hour, then renaming them will take a lot more. I don't think the *rename* command is the optimal solution.

So, start a new thread in the *Programming Talk* forum. You will get better answers there.

[s]EDIT: If you start a new thread, please post a link to it here. Thanks![/s]

EDIT2: never mind. it's here: [thread]1625184[/thread]

---

### Post by thenickdude on 2010-11-18
Thanks.

---

