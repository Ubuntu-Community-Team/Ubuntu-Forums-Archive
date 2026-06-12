---
title: "got root?  i don't..."
date: 2006-02-17
forum: General Help
---

### Post by ingriffiths on 2006-02-17
Ok...I'm new again to linux, it's been since college since i ran it.  I'm running breezy badger now and when i installed it it never asked for a root password...and now i can't su to root or reboot, or install anything.
any ideas?

---

### Post by Delkster on 2006-02-17
Yes. Instead of an actual root account, the default policy in Ubuntu is to use sudo for gaining root privileges.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-02-17
You may also want to read the third link of my signature.

---

### Post by uopjohnson on 2006-02-17
Ubuntu does not use root... well what it actually does is generates a random password instead of allowing you to specify a root password.  You should use the sudo command to run anything you want to run as root and just type in your own user password when asked.  The first user created is automatically placed in the admin group which has access to sudo.
You can also do sudo su to get root access.  
It is a bit of a paradigm shift for those of us used to using a root terminal most of time, but it is much safer for new folks.
There is an expanation on the wiki at
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by ingriffiths on 2006-02-17
Wow, i forgot how much more intelligent and helpful the open source world is...
thanks

---

