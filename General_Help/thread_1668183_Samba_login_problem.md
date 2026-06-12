---
title: "Samba login problem"
date: 2011-01-16
forum: General Help
---

### Post by brad1150 on 2011-01-16
I tried setting up samba on my server so I can access my user /home directory, but when I try to connect to the share (smb://192.168.1.102/gmod) it won't accept my user/pass. I tried this for all the home directories and users and none of them work.

---

### Post by DeMus on 2011-01-16
In your smb.conf file (/etc/samba/smb.conf) you have to write this:
```
[Home-username]
comment Home folder on computername
path = /home/username/
guest ok = yes
```
That way you can access it as a guest without the need of using a password.
**Rem: change username into your own username**

---

