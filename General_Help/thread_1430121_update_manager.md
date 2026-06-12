---
title: "update manager"
date: 2010-03-15
forum: General Help
---

### Post by charreedawn on 2010-03-15
What is the difference between... 

gksu update-manager -d
  and
  update-manager -d

---

### Post by mcoleman44 on 2010-03-15
gksu allows you to run a program as root, without it you dont have root privileges. You could also use gksudo.

---

### Post by 3rdalbum on 2010-03-15
> **charreedawn said:**
> What is the difference between... 

gksu update-manager -d
  and
  update-manager -d

One works, the other one doesn't. The -d argument has meaning in both update-manager AND in gksu, so gksu grabs the argument rather than update-manager.

Update Manager runs fine as regular user, so just use 'update-manager -d'.

If you did need to launch Update Manager as root, you would use:

```
gksudo 'update-manager -d'
```

-d allows you to upgrade to the next version of Ubuntu. If you are already on Karmic, I would NOT recommend you use this until Lucid is in beta, at least. If you wait until Lucid is released, you will be given the option to upgrade in Update Manager anyway, regardless of whether you use the -d argument.

---

