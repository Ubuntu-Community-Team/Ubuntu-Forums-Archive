---
title: "add user to group"
date: 2011-05-15
forum: General Help
---

### Post by engine on 2011-05-15
```
prompt$ sudo adduser newUser groupName
adding user `newUser' to group `groupName'
adding user newUser to group groupName
Done.
prompt$
```

So far so good, but if I then check the group properties via the GUI, newUser has **not** been added to group groupName.

What's going on? Thanks for any advice!

---

### Post by Lars Noodén on 2011-05-15
You need to log out and log back in again for the changes to take affect.  You'll see the new group membership then.

You might also look at the program [usermod](http://manpages.ubuntu.com/manpages/natty/en/man8/usermod.8.html).

---

### Post by bodhi.zazen on 2011-05-16
*Thread moved to **General Help**.*

If you are working on the command line, and do not want to log out and back in, start a new shell

```
bash -l
```

---

