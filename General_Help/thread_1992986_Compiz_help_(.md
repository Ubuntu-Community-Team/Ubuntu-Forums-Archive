---
title: "Compiz help :("
date: 2012-06-01
forum: General Help
---

### Post by Sachin_ruk on 2012-06-01
My compiz settings didnt work so I did the following: 

gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

Now my interface is even worse, compiz has died completely, and even simple tools like snapping do not work. Help :(

The above was suggested in: [http://askubuntu.com/questions/71926/resetting-ccsm-settings](http://askubuntu.com/questions/71926/resetting-ccsm-settings)

---

### Post by fantab on 2012-06-01
From Login Screen press Ctrl+Alt+F1 and you will gain access to the Terminal. Login in to your account and RESET Compiz to its defaults using following command:

```
$ gconftool-2 --recursive-unset /apps/compiz-1
```and then reset Unity:

```
$ unity --reset
```then Reboot.

If that does not solve your problem then you may have to apply/configure all the compiz settings manually.

---

### Post by Sachin_ruk on 2012-06-12
Any hints as to how to apply compiz settings manually?

---

### Post by CatKiller on 2012-06-12
> **Sachin_ruk said:**
> Any hints as to how to apply compiz settings manually?

With CompizConfig-Settings-Manager.

---

### Post by Sachin_ruk on 2012-06-13
Nope, that didn't help might wait for ubuntu 12.10 to fix the problem (fingers crossed).

---

