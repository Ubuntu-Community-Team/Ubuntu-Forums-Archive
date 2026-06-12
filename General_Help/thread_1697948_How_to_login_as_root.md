---
title: "How to login as root"
date: 2011-03-01
forum: General Help
---

### Post by vivekbourne on 2011-03-01
I am using Ubuntu 10.04 netbook edition.can anybody tell me how to login as root. i m not able to do so.

---

### Post by wojox on 2011-03-01
You can just use sudo to gain access. Also read [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Kirboosy on 2011-03-01
I agree with WoJox, just use sudo. Only in rare situations you have to use root.

---

### Post by WorMzy on 2011-03-01
```
sudo -i
```

...will get you a root shell. You should only need it in very rare circumstances though (e.g. accessing a folder that only root can access).

---

