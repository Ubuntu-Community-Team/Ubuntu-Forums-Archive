---
title: "Rsync error"
date: 2006-06-12
forum: General Help
---

### Post by barrowdene on 2006-06-12
I am having trouble with rsync, and get the following error

Command: rsync -arv localhost:/home/admin/data 10.20.20.1:/home/admin/data

Then i get the following error below
Error: rsync: mkdir "/home/admin/10.20.20.1:/home/admin/data" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c (422)


Can anybody help ..... I have a got the syntax correct for rync ?

---

### Post by beercz on 2006-06-12
[QUOTE=barrowdene]I am having trouble with rsync, and get the following error

Command: rsync -arv localhost:/home/admin/data 10.20.20.1:/home/admin/data

Then i get the following error below
Error: rsync: mkdir "/home/admin/10.20.20.1:/home/admin/data" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c (422)


Can anybody help ..... I have a got the syntax correct for rync ?[/QUOTE]
To start with, perhaps you need to check the following:
Do you have the relevant permissions on machine 10.20.20.1?
Have you set up ssh correctly on both machines, so that login to 10.20.20.1 from localhost is automatic - i.e. using ssh's public and private key exchange to allow secure remote connections to 10.20.20.1?
When you ping 10.20.20.1 from localhost, are you getting replies?

Good luck.

---

