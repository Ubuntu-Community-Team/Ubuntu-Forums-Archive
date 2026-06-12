---
title: "can not delete folder on portable disk"
date: 2009-11-14
forum: General Help
---

### Post by tanyeun on 2009-11-14
hi guys,

I have some trouble delete folders on my portable disk
it's in NTFS format
I am not sure if it causes the problem
bcs I don't have that trouble before

```
sudo rm -rf folder
```

even if I use super user still can not delete file
anyone has solutions?
the weirdest thing is that all the file deleted
but left the folders

thx,

David

---

### Post by ajgreeny on 2009-11-14
Try ```
sudo rmdir /folder
```It may simply be that you missed the / in the name, but **rmdir** is safer in any case, and I would recommend it instead of just rm, though you may need to empty the directory first using ```
rm/folder/*
```

---

### Post by tanyeun on 2009-11-14
```
sudo rmdir /folder 
```
does that mean to remove the directory under the root path "/" 
named folder?
I tried but the problem still there
plus, I need to delete the folder in the portable disk
which is under the path: /media/portable_disk
any ideas?

---

### Post by mj10c on 2009-11-14
This ought to do the trick:
```
sudo rm -vfr /media/portable_disk/folder
```
If it still doesn't work then maybe there is some permission issue which may have to be dealt with.

---

### Post by tanyeun on 2009-11-15
it doesn't work
I think it might be the problem with NTFS format
but I don't know how to deal with it

---

### Post by tanyeun on 2009-11-15
btw the error msg is as follows:
```
sudo rm -rf /media/portable_disk/folders/
```
rm: cannot remove directory `/media/portable_disk/folders/sub/': Directory not empty
....

---

### Post by ajgreeny on 2009-11-15
So empty the folder first
sudo rm -rf /media/portable_disk/folders/sub/*

---

### Post by tanyeun on 2009-11-15
they all empty
only left the folders

$sudo rm -rf /media/portable_disk/folders/sub/*
$sudo rmdir /media/portable_disk/folders/sub/ 
rm: cannot remove directory `/media/portable_disk/folders/sub/': Directory not empty

---

### Post by ajgreeny on 2009-11-15
Are you sure there are no hidden files in there? Otherwise I'm baffled.

---

### Post by tanyeun on 2009-11-15
yes, it is really weird 
$ls -a /media/portable_disk/folders/sub/ 
. ..

---

