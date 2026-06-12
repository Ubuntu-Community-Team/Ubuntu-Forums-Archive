---
title: "Disable group login"
date: 2010-05-06
forum: General Help
---

### Post by juddernaut on 2010-05-06
Hi, I am running Ubuntu Server and I am wondering how to disable a whole group from logging in.  I know that I can disable whole accounts with 

sudo passwd -l xxxx

but how can I disable a whole group from logging in?

---

### Post by sisco311 on 2010-05-06
Hi and welcome to the forums!

Hmmm, I think you need to create [pam]("http://www.kernel.org/pub/linux/libs/pam/") rule for that. Append the /etc/pam.d/login file with something like:
```
auth    required       pam_succeed_if.so user notingroup **nologin**
```
where **nologin** is the name of the group.

---

