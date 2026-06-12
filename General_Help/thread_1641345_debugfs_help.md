---
title: "debugfs help"
date: 2010-12-08
forum: General Help
---

### Post by COKEDUDE on 2010-12-08
Take a look at this. 

```
~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  4.2G  4.9G  47% /
none                  1.6G  360K  1.6G   1% /dev
none                  1.6G  1.7M  1.6G   1% /dev/shm
none                  1.6G   92K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
/dev/sda6              29G  9.4G   18G  35% /home
/home/bob/.Private     29G  9.4G   18G  35% /home/bob
/dev/sdb7             232G   99G  133G  43% /media/Part 3
/dev/sdb8             232G   73M  232G   1% /media/Part 4
/dev/sdb1             5.1G   29M  5.0G   1% /media/Hi
/dev/sdb5             232G  231G  1.1G 100% /media/Part 1
/dev/sdb6             232G   24G  209G  11% /media/Part 2
/dev/sdc1             190G  154G   37G  81% /media/26B085D5B085AC3D

```

I am trying to to use debugfs to check out "/home/bob/Desktop". So how would I go about doing that? I tried all of these. None of these were able to see "/home/bob/Desktop" when I tried to cd to it. 

```
debugfs /dev/sda6
debugfs /dev/sda1
debugfs /home/bob/.Private
```

---

### Post by COKEDUDE on 2010-12-11
Does anyone have any ideas?

---

