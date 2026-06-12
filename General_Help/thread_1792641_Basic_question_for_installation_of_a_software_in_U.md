---
title: "Basic question for installation of a software in Ubuntu"
date: 2011-06-28
forum: General Help
---

### Post by lemontree45 on 2011-06-28
open /etc/ld.so.conf in your favourite editor (as root) and add /usr/local/lib on a line by itself.

What are the commands to do this. Please help asap. Thanks

---

### Post by dethorpe on 2011-06-28
Sounds like instructions to edit a file but as root rather than yourself due to you not having permissions to write to it.
 
So from the command line in the terminal type:
 
```
 
$ gksudo gedit /etc/ld.so.conf 

```
 
You will be promted to enter your password, so do so. The editor shoud then start, you can then add the line to the file, save and exit. Job done.
 
(can replace "gedit" with any other GUI editor you want to use)
 
Hope that helps

---

### Post by lemontree45 on 2011-06-28
Thank you :)

---

