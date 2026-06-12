---
title: "Run bash"
date: 2009-09-12
forum: General Help
---

### Post by coffeecake on 2009-09-12
How do i run bash at startup so that i can have root access to the system

---

### Post by coffeecake on 2009-09-12
How do i edit grub so that it would load the terminal as superuser?

---

### Post by yabbadabbadont on 2009-09-12
Once in the terminal, run ```
sudo -i
```

---

### Post by imhotep59 on 2009-09-12
Your question is unclear.
What do you want to do exactly ? You can launch a terminal automatically when your session start (insert gnome-terminal in the starting programs of your session) but if you want to run it as a root you will have to use the command sudo thereafter. 
I think it can be dangerous to start automatically a terminal as a root at the beginning of the session.

---

### Post by coffeecake on 2009-09-12
When system boots  i need run terminal instead of init process

How do i do that?

---

### Post by coffeecake on 2009-09-12
How do i add an automatic program startup entry to the .bash_login file

---

### Post by bapoumba on 2009-09-12
I have merged several threads in here.
To say the least, your questions are quite obscure..

---

### Post by 3rdalbum on 2009-09-12
> **coffeecake said:**
> When system boots  i need run terminal instead of init process

How do i do that?

Edit the GRUB line so it has the phrase:

```
init=/bin/bash
```

Instead of bringing up the system with init, it immediately brings up a terminal.

---

