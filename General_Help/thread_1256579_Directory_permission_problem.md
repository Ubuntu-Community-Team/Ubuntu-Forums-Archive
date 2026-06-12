---
title: "Directory permission problem?"
date: 2009-09-02
forum: General Help
---

### Post by cpthk on 2009-09-02
Hi:

The directory permission suppose to be able to rename, create new, and delete if I have write permission to that directory. But when I tested it, it's not true in ubuntu. 

This is my directory permission in short:
```

drw------- test test dir
test@test$

```

I really have to gain execute permission for me to rename, add, or delete file in the directory. What's wrong with this?

---

### Post by blueridgedog on 2009-09-02
Execute permissions on directories in Linux file systems (Unix as well) are required in order to enter into a directory and access it or files in it in any way.

---

### Post by fluffman86 on 2009-09-02
no, you shouldn't need execute permissions unless you are actually executing an executable file.  like a binary file or a shell script or a python script or something.  

That said, if you're looking to change the permissions, use the chmod command.
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by blueridgedog on 2009-09-02
> **fluffman86 said:**
> no, you shouldn't need execute permissions unless you are actually executing an executable file. 

Without execute permission on a directory you can not enter it or alter the contents of it.  Here is a great overview of file permissions:

[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

### Post by cpthk on 2009-09-03
I have noticed many documentations online are wrong. Even ubuntu's docs.

Make an example: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
The third table in this page shown the directory permissions. It state write permission allow us to create new, and delete. The truth is not.

---

