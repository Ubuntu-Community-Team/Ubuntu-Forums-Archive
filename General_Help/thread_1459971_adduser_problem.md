---
title: "adduser problem"
date: 2010-04-22
forum: General Help
---

### Post by ub007 on 2010-04-22
Hi ,

I created a new user

/etc/passwd

> joe:x:1005:0::/home/joe:/bin/bash

also added him to the group root

vi /etc/group
> root:x:0:root,joe


when i do

su joe

gives me
> ERROR: NO LOGNAME

Strange, any ideas??

---

### Post by zvacet on 2010-04-22
To create new user 

```
sudo adduser <username>
```

and to add it to the group

```
sudo adduser <username> <groupname>
```

---

### Post by ba_saish on 2010-04-23
If you are not used to the command line you can do it in GUI too. 

system->administration->"users and groups" 

click on the "unlock" it using your current log in password. 
then "add user " button should get enabled.

---

