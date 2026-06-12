---
title: "Config error after upgrade to Dapper"
date: 2006-06-26
forum: General Help
---

### Post by Seth Williamson on 2006-06-26
I went from Breezy to Dapper via just changing my sources.list.  Took a hell of a long time to do it on my prehistoric dial-up connection.

Everything seems to work fine, but today when I changed to root (I prefer having a root account instead of using sudo), I got this error message which I've never seen before:

seth@orthobox:~$ su
Password:
configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)

It went ahead and changed me to root, but I don't understand what these error messages mean.

Can anybody tell me what's going on and how to fix it?

Seth Williamson
Slings Gap
Franklin County, VA
USA

---

### Post by mlind on 2006-06-26
I think that problem is with /etc/login.defs
Do you have file called /etc/login.defs.dpkg-dist ?

---

### Post by Seth Williamson on 2006-06-27
[QUOTE=mlind]I think that problem is with /etc/login.defs
Do you have file called /etc/login.defs.dpkg-dist ?[/QUOTE]

Yes, I have this file.  Am I not supposed to?  Should I change it in some way?


Seth Williamson
Slings Gap
Franklin County, VA

---

### Post by Ramses de Norre on 2006-06-27
```
sudo mv /etc/login.defs /etc/login.defs.bak
sudo cp /etc/login.defs.dpkg-dist /etc/login.defs
```
I had the same issue and this solves it (too bad I had already edited the file before noticing the dpkg-dist version..)

---

