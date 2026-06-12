---
title: "Is it possible to make ubuntu ask for user password on chosen apps?"
date: 2010-12-18
forum: General Help
---

### Post by vcrpcant on 2010-12-18
Is it possible to make ubuntu ask for user password on chosen apps like Openoffice or Firefox like it does when launching gparted, for example?

---

### Post by dcstar on 2010-12-18
> **vcrpcant said:**
> Is it possible to make ubuntu ask for user password on chosen apps like Openoffice or Firefox like it does when launching gparted, for example?

Gparted and other system tools are launched with sudo privileges, and it is inappropriate to run user applications in that way.

If you don't want users to be able to run certain applications then you may have to play with the Group permissions.

---

### Post by iponeverything on 2010-12-18
Just add wrapper around the program.

something as simple as renaming firefox to firefox.real create a script called firefox that just contains the line: 

```

gksu -u firefox-users --description Firefox firefox.real

```

and set the perms of the script to 711
create a user called firefox-users

---

### Post by vcrpcant on 2010-12-18
> **iponeverything said:**
> Just add wrapper around the program.

something as simple as renaming firefox to firefox.real create a script called firefox that just contains the line: 

```

gksu -u firefox-users --description Firefox firefox.real

```and set the perms of the script to 711
create a user called firefox-users

Thanks iponeverything for your reply.
However, isn't there another method?

---

### Post by iponeverything on 2010-12-18
> **vcrpcant said:**
> Thanks iponeverything for your reply.
However, isn't there another method?

there are probably at least 10 different ways it could be done..

---

