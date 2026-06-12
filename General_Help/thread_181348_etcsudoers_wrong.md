---
title: "/etc/sudoers wrong ????????"
date: 2006-05-24
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-24
hey im a bit confused atm i cant acess root or use sudo to root in terminal becuase i get this  ```
daniel@dappertest:~$ sudo su
sudo: /etc/sudoers is mode 0777, should be 0440
daniel@dappertest:~$ su
Password:
su: Authentication failure
Sorry.
daniel@dappertest:~$ chmod 440 /etc/sudoers
chmod: changing permissions of `/etc/sudoers': Operation not permitted
daniel@dappertest:~$ su
Password:
su: Authentication failure
Sorry.
daniel@dappertest:~$

```


ne help coz i cant continue nething i am doing while this is happeneing

---

### Post by LORD_PoLvO on 2006-05-24
bump*

---

### Post by LORD_PoLvO on 2006-05-24
fixed it i had to go into my breezy boot and mount the dapper hdd and do a chmod from there lol FIXED *congradualtes self*

---

### Post by ifokkema on 2006-05-25
Hi,

Please note that Ubuntu doesn't set a root password for itself. You need to use 'sudo' followed by the command you want to run.
```
chmod 440 /etc/sudoers
```
should've gotten you working.

Ivo

---

