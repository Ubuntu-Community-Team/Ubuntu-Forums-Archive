---
title: "Can't access directory as member of a group with rwx permission"
date: 2009-09-05
forum: General Help
---

### Post by narnie on 2009-09-05
Hello,

I _THOUGHT_ that I understood permissions in UNIX but have not needed something like this before.

I have created a directory /share/ with root as owner (doesn't matter who the owner is tho I get the same result) and changed its group to "share." The directory has rwx permissions, but I can't access it as a regular user who is in that "share" group. See the follow output (I've proven membership of "share" with the members and id listing):

```
user1@toshiba-laptop / $ ls -ldp sh*
drwxrwx--- 2 root share 4096 2009-09-05 13:52 share/

user1@toshiba-laptop / $ members share
share user1 user2

user1@toshiba-laptop / $ id -nG user1
user1 adm dialout cdrom plugdev lpadmin admin sambashare vboxusers hamachi share


user1@toshiba-laptop / $ ls share/
ls: cannot open directory share/: Permission denied
user1@toshiba-laptop / $ 

user1@toshiba-laptop / $ cd share/
bash: cd: share/: Permission denied
```

What am I missing?

With thanks,
Narnie

---

### Post by relay_man on 2009-09-06
Hello narnie

From /~     Could you post the output of:

ls -la

---

### Post by relay_man on 2009-09-06
You may also want to read this:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1258561&highlight=directory+permissions](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1258561&highlight=directory+permissions)

---

