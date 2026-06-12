---
title: "Accessing permissions to another hard drive"
date: 2009-11-26
forum: General Help
---

### Post by Gene T on 2009-11-26
My friend's hard drive crashed using Ubuntu.  I can access it from my Ubuntu 9.10 machine.  I am trying to retrieve his files, but have no permissions.  Is it possible to gain permission and save his files?
 
Gene T

---

### Post by audiomick on 2009-11-26
you need something like

```
gksudo cp
```

whereby gksudo gives you root priviliges, which should mean you can get access to the files, as far as I know. and cp is the command to copy.

This is not all of it!!

do

```
man cp
```

to get the manual pages for cp, which will tell you how to specify source and destintation

---

