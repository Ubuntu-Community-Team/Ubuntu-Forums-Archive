---
title: "Public files"
date: 2011-03-13
forum: General Help
---

### Post by Spyderkid on 2011-03-13
If I move a file to the Public folder does that mean other users can see and access it them (and how because I want to know if this is the case). Also if this doesn't happen is there somewhere I can move files to so other users can see them (all the home folders are encrypted)

---

### Post by mörgæs on 2011-03-13
The name 'Public' has no meaning in regard to access control. You need to use **chmod** as described in the handbook in my signature.

---

### Post by grahammechanical on 2011-03-13
What Public folder are you talking about? I do not have such a folder. Is it to do with Ubuntu One? If so, then the only people that would have access to the files in that folder will be those people that you have specifically allowed access to it. 

Regards.

---

### Post by Old_Man_Unix on 2011-03-13
During a "standard" installation, Ubuntu creates a number of visible directories (folders) within the initial user's Home directory.  It creates essentially the same structure  for every added new user.  So you will see folders with names like Documents, Pictures,  Music, etc.  One of the standard folders is named Public.  It has a different emblem associated with its icon,  but in all essentials it is just another folder with the "standard" permissions.  

Of course, the name might suggest a particular use for that folder, just as Documents or Music might also suggest a use.  But that is up to you.

---

### Post by mcduck on 2011-03-14
> **Spyderkid said:**
> If I move a file to the Public folder does that mean other users can see and access it them (and how because I want to know if this is the case). Also if this doesn't happen is there somewhere I can move files to so other users can see them (all the home folders are encrypted)

IF the home directories are encrypted, then no mater what you do, the subdirectories wll not be accessible to other users.

However you could create a new shared directory somewhere outside of /home, make it accessible to all users and then symlink it into user's homes.

(If you are not using te "Public" directory for anything, you could of course change *that* into the symlink that points to this shared directory. Not that it would make any other difference tan pretty special icon and a nice name... :D)

---

### Post by Spyderkid on 2011-03-14
How could I make a folder under home, which would have to have no permissions to access (A.K.A no sudo or sudo su)

---

### Post by Spyderkid on 2011-03-16
I've made a folder under home called shared which can only be accessed by root because i had to use sudo to make it. 

How can i change it so anyone can access?

---

### Post by mcduck on 2011-03-16
> **Spyderkid said:**
> I've made a folder under home called shared which can only be accessed by root because i had to use sudo to make it. 

How can i change it so anyone can access?
This will give everyone read & write access to that directory:
```
sudo chmod a+rw /home/shared
```

---

### Post by r-senior on 2011-03-16
@mcduck: Should that be chmod rather than chown?

---

### Post by Morbius1 on 2011-03-16
> **Spyderkid said:**
> I've made a folder under home called shared which can only be accessed by root because i had to use sudo to make it. 

How can i change it so anyone can access?
Define access.

Everyone can add to or delete from that shared directory?

Everyone can do the above and also edit each others files?

This might help: [http://ubuntuforums.org/showpost.php?p=10504171&postcount=11](http://ubuntuforums.org/showpost.php?p=10504171&postcount=11)

---

### Post by mcduck on 2011-03-16
> **r-senior said:**
> @mcduck: Should that be chmod rather than chown?

oh, you are right... Chmod of curse. :D

---

