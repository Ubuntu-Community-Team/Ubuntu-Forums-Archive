---
title: "how can I set permissions for directories?"
date: 2009-10-27
forum: General Help
---

### Post by yanvolking on 2009-10-27
Hello Community,

I have recently discovered the **chmod** command for setting file permissions.

but I need to know how to do the same for directories.

 		$ **chmod g+x anyfile**
"anyfile" being a file;
works

but 

$ **chmod g+x anydirectory**
 "anydirectory" being a directory;

does not work

what are the instructions for setting permissions for directories?

Thanks

---

### Post by alphaniner on 2009-10-27
It should work.  Could you copy'n'paste the output when you try to use it with a directory?

---

### Post by QLee on 2009-10-27
[QUOTE=yanvolking]
what are the instructions for setting permissions for directories?[/QUOTE]

Edit: Does root own that dir?

This will help:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

The community documents have lots of good info for lots of things you might choose to do.

---

### Post by mcduck on 2009-10-27
> **yanvolking said:**
> Hello Community,

I have recently discovered the **chmod** command for setting file permissions.

but I need to know how to do the same for directories.

 		$ **chmod g+x anyfile**
"anyfile" being a file;
works

but 

$ **chmod g+x anydirectory**
 "anydirectory" being a directory;

does not work

what are the instructions for setting permissions for directories?

Thanks

It works exactly like you tried.

But keep in mind that, for example, adding execute permission to a directory doesn't mean adding execute permission to files inside it. It allows executing the directory itself (which is actually the default setting, since you need to be able to execute the directory to list files inside it.)

---

### Post by yanvolking on 2009-10-27
Hi Guys, thanks for the reply.  Problem solved for directories on my PC.  now I would like to change permissions of a whole external drive such as an external HDD or USB stick.  Here the chmod command seems to work, ie with the -v command the progress  list says that the directories and files have been given the new settings, but on physically checking the status of each file, it seems nothing has happened.  Any suggestions?

---

### Post by sisco311 on 2009-10-27
FAT and NTFS partitions don't support unix/linux type file permissions.

You can set the ownership(uid,gid) and permissions for all files and directories at mount time.

---

### Post by yanvolking on 2009-10-27
OK thanks about the bit on FAT and NTFS partitions.

---

