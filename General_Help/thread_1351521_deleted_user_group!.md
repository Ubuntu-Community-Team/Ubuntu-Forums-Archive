---
title: "deleted user group!"
date: 2009-12-10
forum: General Help
---

### Post by ericosuave on 2009-12-10
I was in ubuntu and deleted a group... however, some of the files that the group was associated with still have a group name of 1002??

my question is, how can I re-associate the group name with this number?

thanks!

---

### Post by sisco311 on 2009-12-10
1002 is the [group identifier (GID)]("http://en.wikipedia.org/wiki/Group_identifier").

You can create a new group with gid 1002:
```
sudo addgroup --gid 1002 **groupname**
```

---

### Post by ericosuave on 2009-12-10
sweet! thanks thats what i was looking for!! now how can i add myself to that group?

---

### Post by SuperSonic4 on 2009-12-10
```
sudo gpasswd -a *username* **groupname**
```

---

### Post by sisco311 on 2009-12-10
You can use the GUI: System -> Administration -> Users and Groups
or:
```
sudo adduser user group
```
where user is your login name and group is the name of the group.


EDIT:
@SuperSonic4 

+1 for gpasswd; adduser is a scrip, in non-Debian based distributions may not work.

EDIT2: 
@ericosuave

To activate the user's membership in the new group, log out and log back in the user.

---

### Post by ericosuave on 2009-12-10
perfect! thanks guys.. i used the gpasswd method since he responded before you did. but either worked... im not using the GUI, just cmd line.

---

