---
title: "gain sudo back"
date: 2011-08-04
forum: General Help
---

### Post by koszta on 2011-08-04
Hi,

I accidentally removed myself from admin group. I did usermod -G without -a ... Now is there a way to fix this without rebooting to recovery mode ? I am in root group, but not root himself. 

```
$id
uid=1000(kosta) gid=1000(kosta) groups=0(root),1000(kosta)

```

---

### Post by Lampi on 2011-08-04
using kubuntu this should be easy:

@ the kdm login screen hit alt+n to open a tty shell
login as root
adduser koszta admin
exit

wait a few seconds, kdm will open again

---

### Post by dino99 on 2011-08-04
[http://answers.oreilly.com/topic/1510-how-to-configure-ubuntu-users-groups/](http://answers.oreilly.com/topic/1510-how-to-configure-ubuntu-users-groups/)

---

### Post by sisco311 on 2011-08-04
> **koszta said:**
> Hi,

I accidentally removed myself from admin group. I did usermod -G without -a ... Now is there a way to fix this without rebooting to recovery mode ? I am in root group, but not root himself. 

```
$id
uid=1000(kosta) gid=1000(kosta) groups=0(root),1000(kosta)

```

No, unless you enabled the root account or have access to another admin account.

---

