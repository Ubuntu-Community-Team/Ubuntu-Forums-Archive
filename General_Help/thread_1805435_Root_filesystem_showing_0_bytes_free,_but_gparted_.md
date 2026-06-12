---
title: "Root filesystem showing 0 bytes free, but gparted showing 450mb free!!!"
date: 2011-07-16
forum: General Help
---

### Post by ashimjgec on 2011-07-16
out put of "df -k"

root@bt:~# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3              9842848   9401732         0 100% /
none                    987880       384    987496   1% /dev
none                    995720       164    995556   1% /dev/shm
none                    995720        64    995656   1% /var/run
none                    995720         4    995716   1% /var/lock
none                    995720         0    995720   0% /lib/init/rw
/dev/sda8              2063472    172128   1786524   9% /home
/dev/sdb1              7897072   4699460   3197612  60% /media/RIK

:confused:
can any body help me???

---

### Post by wildmanne39 on 2011-07-16
Hi, look like you need to resize your partiton, here is a link.
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Wim Sturkenboom on 2011-07-16
As you can see from your output, there is still about 450MB free (9842848 - 9401732 = 441116). The (ext) filesystem allocates about 5% of the diskspace for the root user so the root user can still use the system in case of emergency.

You can run the command *sudo du / --max-depth=1* to see which directories under '/' take a lot of space and clean up from there.

One of the ways to create a bit of extra space is to clean out the package management cache (*sudo apt-get clean* if I'm not mistaken).

PS
Wonder how you got it that full ;)
```

root@desktop-01:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              25G  5.0G   19G  22% /
none                  496M  336K  496M   1% /dev
none                  500M  324K  500M   1% /dev/shm
none                  500M  200K  500M   1% /var/run
none                  500M     0  500M   0% /var/lock
none                  500M     0  500M   0% /lib/init/rw
/dev/sda9             115G   18G   91G  17% /home
/dev/sdb1             925G  137G  779G  15% /photos
root@desktop-01:~# 

```
Probably about 1GB more than a fresh install (on 10.04) and after cleaning the cache.

---

### Post by ashimjgec on 2011-07-16
> **Wim Sturkenboom said:**
> As you can see from your output, there is still about 450MB free (9842848 - 9401732 = 441116). The (ext) filesystem allocates about 5% of the diskspace for the root user so the root user can still use the system in case of emergency.

You can run the command *sudo du / --max-depth=1* to see which directories under '/' take a lot of space and clean up from there.

One of the ways to create a bit of extra space is to clean out the package management cache (*sudo apt-get clean* if I'm not mistaken).

PS
Wonder how you got it that full ;)
```

root@desktop-01:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              25G  5.0G   19G  22% /
none                  496M  336K  496M   1% /dev
none                  500M  324K  500M   1% /dev/shm
none                  500M  200K  500M   1% /var/run
none                  500M     0  500M   0% /var/lock
none                  500M     0  500M   0% /lib/init/rw
/dev/sda9             115G   18G   91G  17% /home
/dev/sdb1             925G  137G  779G  15% /photos
root@desktop-01:~# 

```Probably about 1GB more than a fresh install (on 10.04) and after cleaning the cache.


Actually my os is backtrack 5(based on ubuntu 10.04). so there are lots of things pre installed on it, something like more than 1900 packages.
So, shuld I resize my root partition using live os?:confused:

---

### Post by ashimjgec on 2011-07-16
Ok, guys solved the problem by removing some heavy package.
btw thanks to all. :popcorn:

---

### Post by wildmanne39 on 2011-07-16
> **ashimjgec said:**
> Ok, guys solved the problem by removing some heavy package.
btw thanks to all. :popcorn:
Hi, your welcome! glad you got it fixed.

---

