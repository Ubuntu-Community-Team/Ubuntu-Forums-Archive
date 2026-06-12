---
title: "Help!! kill signal kills me"
date: 2010-03-03
forum: General Help
---

### Post by j34j34 on 2010-03-03
Hello I would need your advice.

listen!! I made an application following my boss order.
When starting an application, it sets LCD on.
When finishing an application, it sets LDC off.

The problem is that application is killed by Kill signal from other module.
Above all, it can't set LCD off when it is killed by Kill signal.

Are there any way that application handles routine for LCD off when kill signal happen?

Thanks

---

### Post by r_s on 2010-03-03
why don't you try kill -9 *pid*.

---

### Post by rnerwein on 2010-03-03
hi
first of all: kill -9 not a good idea. -9 is the kiss of death. the application has no change to react !
second - a good application should be desingned to cleanup all his open files, buffers etc.
as normaly a application should have to know what's to do when receiving SIGTERM ( signal 15 ).
even the system sends a SIGTERM to all processes before it is using the signal SIGKILL.
even in shell scripts you can handle signals via. the "trap" call very at the begining of the script.
hope this helps a little bit.
ciao

---

