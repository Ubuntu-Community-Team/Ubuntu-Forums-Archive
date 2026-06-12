---
title: "Perplexing Permissions Problem"
date: 2010-01-30
forum: General Help
---

### Post by magellanic on 2010-01-30
Hello :)

SOLVED: Had to logout & log back in again for changes to take effect :D


Is anyone able to work out why there is a permissions error in this code?

Bearing in mind sigma is a member of the group utxd, and utxd owns /home/rdmn??

```
sigma@orpheus:~$ ls /home/rdmn
sigma@orpheus:~$ ls -l /home
total 11
drwxr-xr-x 7 sigma        sigma       4096 Jan 30 04:52 sigma
drwxrwxr-x 2 rdmn         utxd        4096 Jan 30 04:55 rdmn
sigma@orpheus:~$ cat /etc/group | grep utxd
utxd:x:1004:rdmn,sigma
sigma@orpheus:~$ mkdir /home/rdmn/ffs
mkdir: cannot create directory `/home/rdmn/ffs': Permission denied
sigma@orpheus:~$
```Thanks alot for any help :)

```
Linux orpheus 2.6.24-24-xen #1 SMP Tue Aug 18 18:15:39 UTC 2009 x86_64 GNU/Linux
```

---

