---
title: "MySQL crash and can't get it back up"
date: 2011-12-30
forum: General Help
---

### Post by Ephemeral on 2011-12-30
Hey !

I run a game server, which uses MySQL (quite a few simultaneous connections) and last night we experienced a crash. Apparently the MySQL server went down, and thus the game itself went down.

The thing is, I have no idea how to get it back up, and can't seem to find any solution.. :(

```
/etc/init.d/mysql start
```
gives me :
```
root@ks209052:/var/log/mysql# /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Job failed to start

```


and :
```
mysql -u root -p
```
just gives me :
```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
```

So I looked it up and a lot of people say to create a mysqld.sock file, chmod it 775 and chown it to mysql, which is what I did, but to no avail..
```
root@ks209052:/# cd /var/run/mysqld
root@ks209052:/var/run/mysqld# touch mysqld.sock
root@ks209052:/var/run/mysqld# ls
mysqld.sock
root@ks209052:/var/run/mysqld# chmod 775 mysqld.sock
root@ks209052:/var/run/mysqld# ls -l
total 0
srwxrwxrwx 1 mysql mysql 0 2011-12-30 17:09 mysqld.sock
root@ks209052:/var/run/mysqld# chown mysql:mysql mysqld.sock
root@ks209052:/var/run/mysqld# ls -l
total 0
srwxrwxrwx 1 mysql mysql 0 2011-12-30 17:09 mysqld.sock
root@ks209052:/var/run/mysqld# mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

```

Any clues to this ?

Mark


**Quick edit:** df -h shows me this :
```

Filesystem            Size  Used Avail Use% Mounted on
rootfs                9.7G  9.3G     0 100% /
/dev/root             9.7G  9.3G     0 100% /
/dev                   12G  164K   12G   1% /dev
none                   12G     0   12G   0% /dev/shm
none                   12G  112K   12G   1% /var/run
none                   12G     0   12G   0% /var/lock
none                   12G     0   12G   0% /lib/init/rw
/dev/sda2             1.8T  154G  1.6T   9% /home
tmpfs                 500M  427M   74M  86% /home/minecrafteurope/minecraft/Astyxia/Astyxia
tmpfs                 500M  351M  150M  71% /home/minecrafteurope/minecraft/Astyxia/orebfuscator_cache

```

Could it be because rootfs is full ?

---

### Post by Habitual on 2011-12-30
> **Ephemeral said:**
> ,...Could it be because rootfs is full ?

Almost certainly.

---

### Post by Ephemeral on 2011-12-30
> **Habitual said:**
> Almost certainly.

Right, so how do I resize it ?

---

### Post by Habitual on 2011-12-30
boot up with a LiveCD that has gparted.

---

### Post by Ephemeral on 2011-12-30
> **Habitual said:**
> boot up with a LiveCD that has gparted.

The problem is it's a server, the only access I have is through SSH :/

---

### Post by Ephemeral on 2011-12-30
Is there no way I can free some space ? 9Gigs seems huge oO
Edit : /var/lib contains all of my MySQL databases, a total of over 7G, could that be the problem ?
Is there no way to change where MySQL stores it's data ?

Edit again : Aaaaaaaaand... VICTORY
Took me forever to find the problem, but yeah, rootfs was causing it.
So I edited /etc/mysql/my.cnf, changed where the databases were being stored (put it on main partition), and then I could start MySQL again, yay ! :D

---

