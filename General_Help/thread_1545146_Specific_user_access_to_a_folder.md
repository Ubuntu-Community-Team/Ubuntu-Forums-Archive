---
title: "Specific user access to a folder"
date: 2010-08-03
forum: General Help
---

### Post by theotherjustin on 2010-08-03
Hi

I have a group of ten users which are in a group "dept". I would like to create a folder which allows only four of the users in the group "dept" to have rwx privileges but all other users cannot rwx.

Is this possible?

Many thanks.

---

### Post by leorolla on 2010-08-03
Create a group named whatever, add these four users to the whatever group, and run
```
chown -R yourname:whatever foldername
```
Then give the group permissions you wish to these files...

Unless there is a file that is intened to be executed, just give rw, it's much safer. Directories need to have rwx, though.

---

### Post by theotherjustin on 2010-08-03
Is it that simple? Many thanks!

I did think of doing this but was worried about adding users to another group i.e. users being members of more than one group. But thanks.

Apologies for sounding stupid, but what is the best way of creating a group and adding the users to it?

---

### Post by hudsonl on 2010-08-03
> **theotherjustin said:**
> Hi
 
I have a group of ten users which are in a group "dept". I would like to create a folder which allows only four of the users in the group "dept" to have rwx privileges but all other users cannot rwx.
 
Is this possible?
 
Many thanks.
 
1. Create the group and add users to it (name the group something appropriate)
 
> sudo addgroup newdept
> sudo adduser user1 newdept
> sudo adduser user2 newdept
...
> sudo adduser user4 newdept
 
2. Create the directory
 
> mkdir /pathname/dirname
 
3. Change group ownership to the new group for the directory
 
> chgrp newdept /pathname/dirname
 
4. Allow rwx at the group level
 
> chmod 774 /pathname/dirname
 
 
Can also be 770 depending on if you want to block out totally "other"

---

### Post by theotherjustin on 2010-08-03
Brilliant help :D

Cheers.

---

### Post by leorolla on 2010-08-03
> **theotherjustin said:**
> Is it that simple? Many thanks!

I did think of doing this but was worried about adding users to another group i.e. users being members of more than one group. But thanks.

Apologies for sounding stupid, but what is the best way of creating a group and adding the users to it?

By default you already belong to more groups than you might imagine.

---

