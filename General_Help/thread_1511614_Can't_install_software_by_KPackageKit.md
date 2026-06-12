---
title: "Can't install software by KPackageKit"
date: 2010-06-17
forum: General Help
---

### Post by xoomer.ap on 2010-06-17
Hi, everyone.
I mean that - when I'm choosing any soft to install or remove, the authentication was fail.
Despite this, by using "apt-get" command software installs normally.

Before some time I am by my mistake was removed any groups from my linux-account. Now, my account stay in these groups:
```

andrew@xoompc:~$ groups andrew
andrew : andrew sudo virtualbox

```Maybe I need to enter some group for installing software with KPackageKit ?

---

### Post by wojox on 2010-06-17
Looks like you deleted the admin group which you need. See if this helps [Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by xoomer.ap on 2010-06-17
**wojox**, indeed:
[QUOTE=wojox]Looks like you deleted the admin group which you need[/QUOTE]
Entering to this group solved the problem. :)

Big thanks to you!

---

### Post by wojox on 2010-06-17
Your Welcome :p

---

