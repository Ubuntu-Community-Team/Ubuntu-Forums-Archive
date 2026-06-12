---
title: "A software has turned my flash drive's filesystem into read only"
date: 2010-08-05
forum: General Help
---

### Post by starleaf1 on 2010-08-05
Some moments ago, I plugged my drive into a computer with some strange data protection software. It turned my drive's filesystem into read only and now it can neither be formatted nor mounted with write option. I've tried ```
$ sudo dd if=/dev/zero of=/dev/sdb
``` but it doesn't work.
The problem is, the computer and the software that have caused this problem has lost forever. Any solution?

---

### Post by ubunterooster on 2010-08-05
Boot a live CD and then open a terminal to your root filesystem of your install and run```
chmod 770 *
```
Chmod is "Change mode"  for more on chmod, see:[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by starleaf1 on 2010-08-06
> **ubunterooster said:**
> Boot a live CD and then open a terminal to your root filesystem of your install and run```
chmod 770 *
```

 
Excuse me, but I would appreciate if you'd kindly explain what exactly this command does. I already know that [FONT=Courier New]chmod[/FONT][FONT=Verdana] modifies files and directories' mode, but isn't running the[/FONT][FONT=Verdana] command on root dir will modify *all* of the files?[/FONT]
 
And more importantly, I'm running Linux on wubi. The root filesystem on my installation is inaccessible from a Live CD.

---

### Post by ubunterooster on 2010-08-06
On second thought, because some filesystem files, should have different permissions than others, I am not sure whether to stick it at 770 or 771. 770 might have some errors, but 771 can be somewhat of a slight security breach :(

I think I've out thought myself :(
 sorry not reassuring.


















Chmod changes read/write/execute permissions in which  the first digit is owner, second is group (if you use samba shares or such) and the third is "everyone"

1=read
2=write
4=execute
3=read+write
7=read, write, and execute

So a owner of a file and a group assigned to it (if any) can read write and execute to it. but those not assigned to be the owner of a file or a group assigned to it could not read, write or execute.

I would *think* you could go to the c/program files/ubuntu and change it there, but I have not used Wubi for nearly a year.

---

