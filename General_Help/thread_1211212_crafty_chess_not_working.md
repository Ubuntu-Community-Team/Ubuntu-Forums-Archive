---
title: "crafty chess not working"
date: 2009-07-12
forum: General Help
---

### Post by jahhaj on 2009-07-12
I've just tried installing crafty from the synaptic package manager. Installed OK but crafty gives the error message "ERROR, unable to open game history file, exiting" immediately when run.

Readme file supplied with crafty says that user should be added to games group, I believe that's related to the above error. Unfortunately Ubuntu doesn't make adding myself to the games group very easy.

Any suggestions? Are others seeing this problem? I only found one other post with this problem but the answer wasn't helpful.

I'm using 9.04

Thanks.

---

### Post by monodano on 2011-02-14
I had the same problem on 10.10 and after a long search and many trials I figured out that

```
sudo chmod 777 .crafty/
```solves the issue. At least for me with crafty 23.4

So it is all about writing rights to the directory I guess. Maybe one day the installation routine will be fixed.

---

