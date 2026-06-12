---
title: "File permission"
date: 2009-07-26
forum: General Help
---

### Post by Markstar on 2009-07-26
Hi,
I'm trying to set up Ubuntu as a Webserver and can't put my questions about file permissions off any longer:

I have read the [FilePermissions docu]("https://help.ubuntu.com/community/FilePermissions") and I think I got that. However, I am still unsure how to set up a computer for a multi-user environment:

Let's say I have users Apache, Betty, Charlie and Wicky. Now, we have a directory, let's say: /var/www

The default permissions are *drwxr-xr-x  2 root root *, which, if I am correct, is equivalent to 755 and means that root (as the owner of the file) can do everything (which it can anyway, right?), the group root can read and execute while others can also read and execute. 

Now, let's say I have 3 subfolders for Betty, Charlie and Wicky. Apache should have access to each folder, while obviously each user should be able to access their own folder. Also, Betty and Charlie should have access to Wicky's folder, but not to each other's. 

I know how to do it in Windows (either directly or with group permissions), but how would I do it in Ubuntu? From what I can tell, I can assign only one user and one group to each file. :(

Thank you in advance for your help!

---

### Post by bchurchill on 2009-07-26
> **Markstar said:**
> 
The default permissions are *drwxr-xr-x  2 root root *, which, if I am correct, is equivalent to 755 and means that root (as the owner of the file) can do everything (which it can anyway, right?), the group root can read and execute while others can also read and execute. 

That's right.

> **Markstar said:**
> 
Now, let's say I have 3 subfolders for Betty, Charlie and Wicky. Apache should have access to each folder, while obviously each user should be able to access their own folder. Also, Betty and Charlie should have access to Wicky's folder, but not to each other's. 

There are many ways to do this.  Each group can have as many users as you want in it, so one approach would be to make three groups: Betty, Charlie, Wicky and set the groups to the corresponding folders.  You can add the Apache 'user' to all of these groups, Betty and Charlie to their respective groups, and all of these users to Wicky's group.  I'm sure there are other ways too...

You can add a user to a group with

```
sudo usermod -G <group> <user>
```This won't affect the user's primary group.

---

### Post by Markstar on 2009-07-26
> **bchurchill said:**
> Each group can have as many users as you want in it, so one approach would be to make three groups: Betty, Charlie, Wicky and set the groups to the corresponding folders. You can add the Apache 'user' to all of these groups, Betty and Charlie to their respective groups, and all of these users to Wicky's group.Thank you for your answer! I think I'm going to create extra groups for the folders, like so:
groupB - members: Apache, Betty
groupC - members: Apache, Charlie
groupW - members: Apache, Betty, Charlie, Wicky
 
Because the way you suggested it (if I understood you correctly), Apache could then access ALL files from Betty and the rest, wherever they are. 

> You can add a user to a group with

```
sudo usermod -G <group> <user>
```This won't affect the user's primary group.I'm sorry, I don't know what you mean by "primary group". Are you saying that if I add a user to a group, he/she will still be in the old group as well? That would make sense, otherwise a user could only be in one group.  

Anyways, these are the commands I have in mind:
**_Create groups for each folder:_**
groupadd gBetty
groupadd gCharlie
groupadd gWicky
groupadd gAll
**_Add users to the right group:_**
usermod -G gBetty, gCharlie, gWicky, gAll apache
usermod -G gBetty, gWicky, gAll betty
usermod -G gCharlie, gWicky, gAll charlie
usermod -G gBetty, gCharlie, gWicky, gAll wicky
_**Assign the groups to the folders:**_
chgrp gAll /var/www 
chgrp gBetty /var/www/betty
chgrp gCharlie /var/www/charlie
chgrp gWicky /var/www/wicky

Is this correct? Is there anything else I have to consider?

---

