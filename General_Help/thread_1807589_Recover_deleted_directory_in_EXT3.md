---
title: "Recover deleted directory in EXT3"
date: 2011-07-19
forum: General Help
---

### Post by x53x6ex69x67x67x65x72 on 2011-07-19
Hi
I can recover deleted files using "debugfs" & "extundelete" by running:
```
sudo debugfs /dev/sda3
```
and find inode number of deleted file using "ls -d" command and then running:
```
sudo extundelete /dev/sda3 --restore-file <inode#>
```
but when my desired file was in a deleted folder I can't find my desired file inode number using debugfs.
How can I find inode number of files in a deleted directory?

---

### Post by Wayne_V on 2011-07-19
It's been awhile since I've had to use debugfs -- but a directory is basically just a special type of file.  You should find the directory first, undelete that, and then you should be able to cd to it and see the deleted files there.

---

### Post by x53x6ex69x67x67x65x72 on 2011-07-19
> **Wayne_V said:**
> It's been awhile since I've had to use debugfs -- but a directory is basically just a special type of file.  You should find the directory first, undelete that, and then you should be able to cd to it and see the deleted files there.
Hi 
when I try to undelete that directory with:
```
debugfs:  undelete <2711553>
```
I get :
```
<2711553>: Inode is not marked as deleted
```
while "ls -d" says this inode is deleted!

---

