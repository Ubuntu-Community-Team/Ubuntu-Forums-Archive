---
title: "QTdesigner?"
date: 2006-05-09
forum: General Help
---

### Post by GekkeHenk on 2006-05-09
I installed qt3-designer but how can I run the program? :S

---

### Post by louis_nichols on 2006-05-09
Well, if you don't have any shortcuts in the menus, use the command

```
dpkg -L qt3-designer | grep bin
```

to see what executables are in the package. One of them is the app launcher. Actually, it is quite likely that you will only get one.

---

### Post by ukripper on 2007-06-13
> **louis_nichols said:**
> Well, if you don't have any shortcuts in the menus, use the command

```
dpkg -L qt3-designer | grep bin
```

to see what executables are in the package. One of them is the app launcher. Actually, it is quite likely that you will only get one.

Nice one mate. I was just looking for that. Now i can add it to my menu. 

:KS

---

