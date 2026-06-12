---
title: "legit group member cannot ls (permission denied)"
date: 2011-09-09
forum: General Help
---

### Post by misterbiskits on 2011-09-09
Here I have a folder, owned by user 'minecraft' and group 'minecraft'.  Group has full permissions.

```
mike@cham-server:/$ ls -ld /home/minecraft
drwxrwx--- 2 minecraft minecraft 4096 2011-09-09 07:13 /home/minecraft
```Here I have a user belonging to the group 'minecraft'.

```
mike@cham-server:/$ groups mike
mike : mike adm dialout cdrom plugdev lpadmin sambashare admin debian-transmission minecraft
```I am expecting the group member to be able to ls or cd into the folder, but I get a permission denied error...

```
mike@cham-server:/$ ls /home/minecraft/
ls: cannot open directory /home/minecraft/: Permission denied
```Please help me to understand where I am going wrong.

---

### Post by Bodsda on 2011-09-09
> **misterbiskits said:**
> Here I have a folder, owned by user 'minecraft' and group 'minecraft'. Group has full permissions.
 
```
mike@cham-server:/$ ls -ld /home/minecraft
drwxrwx--- 2 minecraft minecraft 4096 2011-09-09 07:13 /home/minecraft
```Here I have a user belonging to the group 'minecraft'.
 
```
mike@cham-server:/$ groups mike
mike : mike adm dialout cdrom plugdev lpadmin sambashare admin debian-transmission minecraft
```I am expecting the group member to be able to ls or cd into the folder, but I get a permission denied error...
 
```
mike@cham-server:/$ ls /home/minecraft/
ls: cannot open directory /home/minecraft/: Permission denied
```Please help me to understand where I am going wrong.
 
Have you logged out and back in after adding the user to this group?
[http://ubuntuforums.org/showthread.php?t=1427158](http://ubuntuforums.org/showthread.php?t=1427158)
 
Bodsda

---

### Post by misterbiskits on 2011-09-09
eureka! 
Thank you very much!  
Thank you for the link as well, I don't like posting questions that have already been answered but my search came up with nothing useful.
Thanks again!

---

