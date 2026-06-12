---
title: "removing user from group"
date: 2011-12-04
forum: General Help
---

### Post by eltiti55555 on 2011-12-04
I created an user and a group, then I added the user to the new group, now I want to delete the user from that same group. How do I do it? Keep in mind that I want to do this using the command line and that I only want to remove that single user from a group without affecting the other groups he belongs to or the group he is being removed from. Thanks! :)

---

### Post by hwttdz on 2011-12-04
**See post 3, it's a better solution**

"groups username" will tell you all the groups the user belongs to. 

"usermod --groups GROUP1[,GROUP2,...[,GROUPN]]]"
will set the user as belonging to those groups and no others.

There is no "remove user from group" flag, so you have to list all those you want them to be in.  If they belong to a lot of groups I'm sure you can use perl to parse the output of users to input for usermod.

---

### Post by papibe on 2011-12-04
You can also use 'gpasswd' like this:
```
sudo gpasswd --delete user group
```
It is a bit safer that usermod because it only removes 'group' from 'user', and it doesn't touch the other groups that 'user' belongs to.

Regards.

---

