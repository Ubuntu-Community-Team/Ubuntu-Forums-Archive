---
title: "help to clean cache memory"
date: 2010-01-24
forum: General Help
---

### Post by david sousa on 2010-01-24
Hey,

I read somewhere that i can clean cache memory with this comand:

```
david@lap:~$ sudo echo 3 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied

```

The problem is that permission is denied as you see... Do you know how solve this?

Thanks...

---

### Post by rnerwein on 2010-01-24
hi
i am runing 9.10 karmic and try your command. on my system it works ( i see this using free )
whats about the permissions of drop_caches or --> /proc/sys/vm/drop_caches (since Linux 2.6.16)
man 5 proc.
ciao

---

### Post by danastasio on 2010-01-24
that is the command to write cache to disk, but, as you found, it does not run under sudo, it needs root,

```
su
sync; echo 3 > /proc/sys/vm/drop_caches
```

However, this takes your cache from RAM (fast) and writes it to the disk (slow) which is why it is not really recommended.

---

### Post by blueshiftoverwatch on 2010-01-24
> **danastasio said:**
> that is the command to write cache to disk, but, as you found, it does not run under sudo, it needs root,

```
su
sync; echo 3 > /proc/sys/vm/drop_caches
```

However, this takes your cache from RAM (fast) and writes it to the disk (slow) which is why it is not really recommended.
I cleared about 4GB worth of cached RAM today using that command and my swap space is only 55MB filled up. If it wrote to the disk wouldn't it be about 4GB filled up?

---

### Post by david sousa on 2010-01-24
thanks danastio, it works!

do you know hao to clean swap?

---

