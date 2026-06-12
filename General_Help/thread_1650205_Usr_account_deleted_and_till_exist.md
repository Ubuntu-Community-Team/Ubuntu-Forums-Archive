---
title: "Usr account deleted and till exist"
date: 2010-12-21
forum: General Help
---

### Post by simsym05 on 2010-12-21
Hi,

I just deleted an account, this is the command used:
#userdel sam1
check:
/home#ls
xxx sam1 xxx

as you can see sam1 still exist with other users, so i checked to login:
/home#cd sam1
/home/sam1#

So itried to delete it again with
/home#userdel -f sam1
and i had the message: sam1 doesn't exist

but with /home#ls
sam1 exist again

Can you please explain to me the problem and how i have o fix it?

Thanks in advance.

Regards

---

### Post by karthick87 on 2010-12-21
You have already deleted the useraccount sam1..So now you should remove the user directory(sam1) manually..

```
 sudo rm -r /home/sam1
```

---

### Post by 3Miro on 2010-12-21
/home/sam1 is a folder that contains some files (what used to be sam1's settings and personal files).

sam1 is the name of a user registered to use the system.

If you userdel sam1, then you remove the user. Sam1 can no longer login and/or do any work on the system. However, userdel doesn't delete sam1's folder as it may contain important information. To remove the folder, you can use the standard command:
```
rm -fr /home/sam1 
```
(probably you need sudo in front of that).

BTW when you cd into sam1's folder, you have not login as sam1. With cd, you are still your user, just working on a different place on the system.

---

