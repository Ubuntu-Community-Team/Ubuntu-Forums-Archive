---
title: "why is my GID 999?  How do I change it?"
date: 2010-03-07
forum: General Help
---

### Post by switch10 on 2010-03-07
I successfully changed my UID from 999 to 1000, so now I can see my name in the log in screen, and in "users and groups".  I had to create another account with admin privileges, and switch it that way.  My GID is still at 999.  I'm not sure if this matters or not.

I can't add myself to a group with this command;
```
 useradd -G vboxusers dave 
```
I get a message saying that the user exists. 

I did manage to add myself to the group with the "users and groups" GUI.

but when I run
```
 id 
```

it doesn't list the group that I've added myself to.

---

### Post by falconindy on 2010-03-07
if you want to add yourself to a group, the best way to do it is to use the 'gpasswd' utility:
```
gpasswd -a <user> <group>
```
Don't forget to log out and back in in order for the changes to take effect.

Not sure why your UID is 999 except that when creating the new users, the first user-defined system user account is given UID 999 (with progressive accounts counting down). Actual users should be starting with 1000 and counting up.

---

### Post by switch10 on 2010-03-07
> **falconindy said:**
> if you want to add yourself to a group, the best way to do it is to use the 'gpasswd' utility:
```
gpasswd -a <user> <group>
```
Don't forget to log out and back in in order for the changes to take effect.

Not sure why your UID is 999 except that when creating the new users, the first user-defined system user account is given UID 999 (with progressive accounts counting down). Actual users should be starting with 1000 and counting up.

haha, I forgot to log out and back in!  

thanks

do you think having a GID of 999 will cause problems in the future, like my UID did?

I have no idea how my UID and GID changed from 1000 to 999.  It happened after I installed slackware.  It was sharing my /home partition.

---

