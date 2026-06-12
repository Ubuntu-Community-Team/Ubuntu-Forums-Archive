---
title: "Start an application in terminal"
date: 2010-04-29
forum: General Help
---

### Post by dragos2 on 2010-04-29
Hi,

I have a binary application that runs only in shell, now I want to open it from another application(Mathematica program) but simply invoking it will start it in memory but not in a shell.

I tryed "bash app" which does not work and "gnome-terminal app" just opens the terminal
without launching that application.

Any idea of how to do this ?


Ps: Its the same thing as in Java when you want to invoke a system command like
ping but you need to do it like this .exec("cmd ping") instead of just ping.

---

### Post by dragos2 on 2010-04-29
Solved with
```
gnome-terminal -x program
```

from that external program :)

---

