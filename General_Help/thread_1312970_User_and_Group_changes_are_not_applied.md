---
title: "User and Group changes are not applied"
date: 2009-11-03
forum: General Help
---

### Post by j-one on 2009-11-03
I got the new Ubuntu. In user settings, i try to change main group for me and another account to "users". It seems to be applied at first - but Nope. When reopening user settings, no difference is made. Also, when trying to delete an account - the same thing happens. Seems to be applied, but not when restarted. Adding a group to a user, however, is applied.

Do I have to say.. I am a newbie in using Ubuntu for home use. At work, however, I develop C++ applications in Linux Red Hat.

---

### Post by cariboo on 2009-11-03
You have to log out and the log back in again in order for group changes to take place.

---

### Post by j-one on 2009-11-03
It doesn't seem to help. I just logged out and in, and no difference. Also, the removed user remains.

---

### Post by sisco311 on 2009-11-03
Not a solution for your problem with users-admin (Users and Groups GUI), but you can use the CLI.

You can change the primary group of an user with the usermod command:
```
sudo usermod -g **users** **username**
```
**users** is the new primary group
**username** is the login name of the user

The group must exist, so you may have to create it:
```
sudo addgroup users
```

You can delete a user with the deluser command:
```
sudo deluser username
```


NOTE: You will have to change the group ownership of the files manually.

i.e.
```
sudo chgrp users /path/to/file
```

or recursively:
```
sudo chgrp users /home/username
```

The commands are well documented in man pages:
```
man **command**
man usermod
...
```

---

### Post by j-one on 2009-11-03
I tried command line instead, to remove a user, and to change main group. That worked.

So GUI for changing users a groups did not work very well. Wonder what is wrong... But I am happy with the command line solution.

/Jocke

---

### Post by sisco311 on 2009-11-03
> **j-one said:**
> I tried command line instead, to remove a user, and to change main group. That worked.

So GUI for changing users a groups did not work very well. Wonder what is wrong... But I am happy with the command line solution.

/Jocke

It's probably a BUG. 

I've found this about deleting users: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/458883]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/458883")

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bugs?start=0]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bugs?start=0")

---

