---
title: "user accounts"
date: 2012-04-04
forum: General Help
---

### Post by netopalis45 on 2012-04-04
I would like to make an account just for remote printing. I would prefer it to be hidden and not have a password if at all possible. The only privilege it would have is printing and ssh. Is there any way of doing this?

---

### Post by cortman on 2012-04-04
Just a few words to steer you in the right direction...

I think first you need to create a new user group. The [addgroup command]("http://manpages.ubuntu.com/manpages/dapper/man8/adduser.8.html") is probably the best option for this. Then you can add a new user using adduser. I think the trick is to specify that the new user is ONLY a member of the "print/ssh" group that you created earlier.

---

### Post by netopalis45 on 2012-04-05
Ok, got that. I would like to restrict that group to just printing and ssh and I don't see any options for that. All I see is which users are going to be in the group.

---

### Post by hughr2005 on 2012-04-05
Hi netopalis45,

this may help: [http://harrykar.blogspot.com/2010/03/ubuntu-users-groups-permissions.html](http://harrykar.blogspot.com/2010/03/ubuntu-users-groups-permissions.html)

---

### Post by cortman on 2012-04-05
I suppose you could use chmod to remove rwx permissions from everything on the filesystem except the printing and ssh binaries. Not sure about dependent files then, though.

---

