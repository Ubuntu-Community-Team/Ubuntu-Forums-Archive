---
title: "Crontab Problem"
date: 2011-01-10
forum: General Help
---

### Post by CampNoNet on 2011-01-10
i am having this problem 
```
Welcome...
Last login: Mon Jan 10 11:05:03 2011 from cpe-72-185-137-85.tampabay.res.rr.com
rangerbob@Athlon:~$ crontab -e
237
01 04 * * * /usr/bin/somedirectory/somecommand
?
```

it not opening the nano screen but under a diffetent account it works fine any help

---

### Post by vcrpcant on 2011-01-10
[SIZE=1]Try one of those:[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]export EDITOR=nano[/SIZE]
or
[SIZE=1]export EDITOR=vi[/SIZE]
[SIZE=1]or[/SIZE]
[SIZE=1]export EDITOR=vim[/SIZE]
[SIZE=1]or 
[/SIZE]
[SIZE=1]export EDITOR=gedit [in ubuntu desktop]
[/SIZE]

then
crontab -e
[SIZE=1]
[/SIZE]

---

### Post by CampNoNet on 2011-01-10
thanks :)

---

