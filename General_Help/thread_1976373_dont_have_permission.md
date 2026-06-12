---
title: "dont have permission"
date: 2012-05-08
forum: General Help
---

### Post by dog-soldier on 2012-05-08
im trying to add the speeddial.ini file to the opera folder on my tablet pc running 12.04 and when i do it says i cant because i dont have permission. 
how do i go about getting permission ?

---

### Post by kc1di on 2012-05-08
> **dog-soldier said:**
> im trying to add the speeddial.ini file to the opera folder on my tablet pc running 12.04 and when i do it says i cant because i dont have permission. 
how do i go about getting permission ?
.ini files are normally windows files.  and are not install able in linux. Unless your using wine. Opera speed dial has always worked for me if opera is installed using opera's ubuntu download file.

---

### Post by dog-soldier on 2012-05-08
> **kc1di said:**
> .ini files are normally windows files.  and are not install able in linux. Unless your using wine. Opera speed dial has always worked for me if opera is installed using opera's ubuntu download file.

thats strange, on both 10.04 and 12.04 my opera folders have .ini files in them.
im adding the speed dial file from my 10.04 machine to my 12.04

---

### Post by Baldrick_NZ on 2012-05-08
It's a bit of a long shot, but worth a crack...

Locate the actual file concerned and check that you do have the permissions to run it. 

Right click over the file, choose Properties, then click on the permissions tab. That should list you as the owner of the file and allow you read-write file access.

If not, report back.

---

### Post by dog-soldier on 2012-05-08
when i click on the permissions tab it says the group is root. i was able to add it in 11.04 butnot 12.04 forsome reason.

---

### Post by Baldrick_NZ on 2012-05-08
> **dog-soldier said:**
> when i click on the permissions tab it says the group is root. i was able to add it in 11.04 butnot 12.04 forsome reason.

Ok, so that would explain why you don't have the permission to run it.

to change ownership from root to you, in terminal```
gksu nautilus
```Then navigate to the file in question. Right click over it and choose 'Properties', then the permission tab again. Under 'Owner' change from root to your user name and whatever folder and file access you require. You should also change the group from root to your user name as well. Click 'Close', and you're done.

---

### Post by dog-soldier on 2012-05-08
> **Baldrick_NZ said:**
> Ok, so that would explain why you don't have the permission to run it.

to change ownership from root to you, in terminal```
gksu nautilus
```Then navigate to the file in question. Right click over it and choose 'Properties', then the permission tab again. Under 'Owner' change from root to your user name and whatever folder and file access you require. You should also change the group from root to your user name as well. Click 'Close', and you're done.

when i right click on the file im unable to change the group.the file i want to replace with will let me change group

---

