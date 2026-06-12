---
title: "Clicking on restart only logs out"
date: 2011-09-18
forum: General Help
---

### Post by joel_gil on 2011-09-18
Using Xubuntu 11.04 64bit on my Inspiron 14R n4110.

As simple as that, everytime i click on "restart" it logs me out, i  have to click restart again from the login screen.
weird.

---

### Post by Toz on 2011-09-18
The problem is that X is crashing and gdm is restarting. This is a known bug ([https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/711571]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/711571") - there are others). I've been able to remediate this problem on my notebook by creating a file called **.xinitrc** in my home directory with the following contents:
```
ck-launch-session startxfce4
```

YMMV.

---

