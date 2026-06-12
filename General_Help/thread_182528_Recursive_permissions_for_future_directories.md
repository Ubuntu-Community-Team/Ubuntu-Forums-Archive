---
title: "Recursive permissions for future directories?"
date: 2006-05-26
forum: General Help
---

### Post by Mr Green on 2006-05-26
I'm wondering if there is a way of telling a directory in Linux that all subdirectories created in the future should automatically have the same permissions as itself.

Example:

/home/share has rwx permissions for "user" and "group" while "other" have no permissions:

drwxrwx---  /home/share

If I create /home/share/testdir I want it to have the same permissions without having to use chmod:

drwxrwx---  /home/share/testdir

Anybody out there know if this is possible?

---

### Post by yanik on 2006-05-26
Here's a unix permission primer:

[http://www.tuxforums.org/forum/viewtopic.php?t=432&sid=736df5a5634f0f4ba712fc873e28fa12](http://www.tuxforums.org/forum/viewtopic.php?t=432&sid=736df5a5634f0f4ba712fc873e28fa12)

If you are already know how it works, simply scroll down to **Per User and System Defaults With umask**

---

