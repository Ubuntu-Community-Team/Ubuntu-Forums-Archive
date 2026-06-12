---
title: "Just installed ubuntu and don't have permissions."
date: 2006-04-28
forum: General Help
---

### Post by pvent on 2006-04-28
I just installed ubuntu  in my machine, and I'm the only user. Yet, it tells me that I'm not the owner (propietary?), so I can't change the permissions to access files.
So, why did this happen? How can I fix this?

---

### Post by salem7 on 2006-04-28
Did u 
**sudo chmod** ..... ?

---

### Post by dermotti on 2006-04-28
Yep you need to precede all commands that require superuser with **sudo**

---

### Post by aysiu on 2006-04-28
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by pvent on 2006-04-28
[QUOTE=dermotti]Yep you need to precede all commands that require superuser with **sudo**[/QUOTE]
I have the X Window GUI, so I don't know how to use the sudo command.
Sorry, I'm a linux newbie :(

---

### Post by bbarrons on 2006-04-28
open a terminal window. anytime you need root permissions you precede the command with sudo. it will ask for a password. you then use your regular password. no need for a root at all.
it would be like this: sudo apt-get update
or whatever you are trying to do...
make sense??
hope this helps
Bill

---

