---
title: "Custom default permissions possible?"
date: 2009-10-12
forum: General Help
---

### Post by viking_maniac on 2009-10-12
I was just wondering; like when you make a new folder or paste files, they all get these default permissions: The owner (you) get full access. The **user** group get read-only access. **Others** get read only access too. This happens all the time.

Is it possible to set other permissions as default? Like if you create a folder or paste a file, you will get these permissions: The owner (you) get full access. The **user** group and **others** get no access.

Is it possible?

---

### Post by zvacet on 2009-10-13
Type in terminal 

```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_advanced_permissions True
```

After that when you right click on folder>properties>permissions you will be able to set permissions as you want with GUI.

---

### Post by StuartN on 2009-10-13
> **viking_maniac said:**
> when you make a new folder or paste files, they all get these default permissions

The default denial of permissions is defined by **umask**. If you run umask it will display a permission mask 0022, which means "remove write permission for group and others". The command **umask -S** displays a more friendly **u=rwx,g=rx,o=rx**. You can deny read (4), write (2) and execute (1) permission by adding these (0-7) for user, group and others.

Placing **umask 0033** in a startup script would define your defaults as no write, no execute for group and others.

---

