---
title: "forbidding the execution of a program for a user"
date: 2010-11-27
forum: General Help
---

### Post by child on 2010-11-27
Hi!
I'd like to enquire about how to forbid the execution of a program for a user or a group.
Do i have to write a script for that or is there some integrated feature?

---

### Post by eric3_14159 on 2010-12-24
The simplest way is to do the opposite.

If you can create a group which everyone allowed to execute the program belong to, then you can set the program to be in that group, and set its permission bits to be rwxr-x--- (750).

---

### Post by matt_symes on 2010-12-24
Hi

Have a look at chmod. It sets the permission bits

From the terminal type.

```
man chmod
```

and look at

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Kind regards

---

