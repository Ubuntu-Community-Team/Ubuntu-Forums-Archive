---
title: "user permission"
date: 2010-02-14
forum: General Help
---

### Post by hilfmir on 2010-02-14
hello, i have recently converted my laptop to ubuntu. 
i am the only user and the owner of the computer but when i try to restore my gimp brushes that i backed up from the windows, it simply says that i dont have the user privilages as i am not the owner.
can someone help me? i have set a password and it does not ask me for the password when i try to move the brushes back

---

### Post by switch10 on 2010-02-14
You need to be root to move some stuff.  If you are using nautilus to move the files, open a terminal and type:

```
 gksu nautilus 
```

it will ask you for a password, and then open up a window where you will be able to move files around.

There is an easier way using the mv command in a terminal, but since you are new to Linux, I think you will be more comfortable with drag and drop.

---

### Post by hilfmir on 2010-02-14
thanks bro ill give this a shot

---

