---
title: "/etc/ssh Permission"
date: 2009-07-11
forum: General Help
---

### Post by dbrine on 2009-07-11
I accidently 777 the /etc/ssh directory (-rwxrwxrwx). I tried to chmod 700 and chmod 600 but when I do that and then goto the ssh directory and run ls -ln it still reads -rwxrwxrwx. What am I doing wrong? Should the permissions be 600 on the directory and files?

---

### Post by spiderbatdad on 2009-07-11
> **dbrine said:**
> I accidently 777 the /etc/ssh directory (-rwxrwxrwx). I tried to chmod 700 and chmod 600 but when I do that and then goto the ssh directory and run ls -ln it still reads -rwxrwxrwx. What am I doing wrong? Should the permissions be 600 on the directory and files?
```
sudo chmod 755 /etc/ssh
```

---

### Post by dbrine on 2009-07-11
when I do that and I run ls -ln it should list the files inside ssh with the correct permission right?

---

### Post by spiderbatdad on 2009-07-11
right. if you want to see perms for /etc/ssh, run ```
ls -l /etc
```and scroll to ssh. Or perhaps ```
ls -l /etc | grep ssh
``` If you run ls -l /etc/ssh, you will see perms for files in /etc/ssh

---

### Post by bernied on 2009-07-11
The files in /etc/ssh do not all have the same permissions. This is one of mine:
```
bernie@shinym:/etc/ssh$ ls -la
total 164
drwxr-xr-x   2 root root   4096 2009-01-22 13:11 .
drwxr-xr-x 102 root root   4096 2009-07-05 19:10 ..
-rw-r--r--   1 root root 125749 2008-07-29 15:33 moduli
-rw-r--r--   1 root root   1595 2008-05-29 21:43 ssh_config
-rw-r--r--   1 root root   1872 2008-07-09 20:23 sshd_config
-rw-r--r--   1 root root   1874 2008-07-05 23:54 sshd_config.original
-rw-------   1 root root    672 2008-07-05 23:54 ssh_host_dsa_key
-rw-r--r--   1 root root    601 2008-07-05 23:54 ssh_host_dsa_key.pub
-rw-------   1 root root   1675 2008-07-05 23:54 ssh_host_rsa_key
-rw-r--r--   1 root root    393 2008-07-05 23:54 ssh_host_rsa_key.pub
```
So the directory is 755, most of the files are 644, but some are 600.

Bernie

---

