---
title: "adding group lp to my user deleted me from sudoers list"
date: 2010-02-09
forum: General Help
---

### Post by skai2701 on 2010-02-09
Hello everybody,
I have a problem: I seem to have deleted myself from sudoers. I do not yet know how that could happen, but it is a fact.
Now, I could start a live Ubuntu and change the sudoers file again, but is that safe ?
Has anybody solved the problem already?

Thanks,

Skai

---

### Post by sisco311 on 2010-02-09
Boot in the Recovery Mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Next time when you use usermod to add a user to a group use the -a flag ;)

```
usermod -aG group username
```
or 
```
gpasswd -a user group
```
or on a debian based system:
```
adduser username group
```

---

