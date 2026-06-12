---
title: "Cannot access folders in var directory after changing permissions."
date: 2010-07-31
forum: General Help
---

### Post by penydaith on 2010-07-31
Hi everyone.  This is my first post here, so I am glad to be here.  :)  Anyway, I have a bit of a problem.

I was changing some permissions in my /var/www directory (I installed apache2), and I accidentally changed the permissions of everything in my /var/ directory.  I changed all of the permissions back (sudo chmod 644 *), but I cannot access ANY directory in /var/ now unless I am root.  If I am not root I always get:  

/var$ cd lib
bash: cd: lib: Permission denied

If I do a detailed listing of all of the folders in the directory, this is what it looks like: 

drw-r--r--  2 root root  4096 2010-07-30 00:57 backups
drw-r--r-- 21 root root  4096 2010-07-30 22:15 cache
drw-r--r--  2 root root  4096 2010-04-13 15:52 crash
drw-r--r--  2 root root  4096 2010-04-29 07:26 games
drw-r--r-- 67 root root  4096 2010-07-30 22:16 lib
drw-r-Sr--  2 root staff 4096 2010-04-23 05:11 local
drw-r--r--  3 root root    60 2010-07-30 22:03 lock
drw-r--r-- 17 root root  4096 2010-07-30 22:15 log
drw-r-Sr--  2 root mail  4096 2010-04-29 07:17 mail
drw-r--r--  2 root root  4096 2010-04-29 07:17 opt
drw-r--r-- 17 root root   680 2010-07-30 22:20 run
drw-r--r--  7 root root  4096 2010-04-29 07:22 spool
drw-r--r--  3 root root  4096 2010-07-30 01:44 tmp
drw-r--r--  3 root root  4096 2010-07-31 00:34 www

I do not know what the 'd' at the beginning of the permissions means, but I am guessing that has something to do with my problem because it doesn't appear in other directory listings.

Anyway, I would like to be able to access my folders again, in particular my www folder, since I like to be able to test my webpages on my own machine.

Thanks in advance for any help.  :)

penydaith

---

### Post by lloyd_b on 2010-08-01
> **penydaith said:**
> Hi everyone.  This is my first post here, so I am glad to be here.  :)  Anyway, I have a bit of a problem.

I was changing some permissions in my /var/www directory (I installed apache2), and I accidentally changed the permissions of everything in my /var/ directory.  I changed all of the permissions back (sudo chmod 644 *), but I cannot access ANY directory in /var/ now unless I am root.  If I am not root I always get:  

/var$ cd lib
bash: cd: lib: Permission denied

If I do a detailed listing of all of the folders in the directory, this is what it looks like: 

drw-r--r--  2 root root  4096 2010-07-30 00:57 backups
drw-r--r-- 21 root root  4096 2010-07-30 22:15 cache
drw-r--r--  2 root root  4096 2010-04-13 15:52 crash
drw-r--r--  2 root root  4096 2010-04-29 07:26 games
drw-r--r-- 67 root root  4096 2010-07-30 22:16 lib
drw-r-Sr--  2 root staff 4096 2010-04-23 05:11 local
drw-r--r--  3 root root    60 2010-07-30 22:03 lock
drw-r--r-- 17 root root  4096 2010-07-30 22:15 log
drw-r-Sr--  2 root mail  4096 2010-04-29 07:17 mail
drw-r--r--  2 root root  4096 2010-04-29 07:17 opt
drw-r--r-- 17 root root   680 2010-07-30 22:20 run
drw-r--r--  7 root root  4096 2010-04-29 07:22 spool
drw-r--r--  3 root root  4096 2010-07-30 01:44 tmp
drw-r--r--  3 root root  4096 2010-07-31 00:34 www

I do not know what the 'd' at the beginning of the permissions means, but I am guessing that has something to do with my problem because it doesn't appear in other directory listings.

Anyway, I would like to be able to access my folders again, in particular my www folder, since I like to be able to test my webpages on my own machine.

Thanks in advance for any help.  :)

penydaith

The "d" at the beginning of the permissions is the "type" - "d" = directory.

Your problem is that you need to have "execute" permission to be able to cd into a directory (unless you're root, of course).  You need for all directories to have permissions of 755 (rwxr-xr-x) rather than 644 (rw-r--r--) as you have now. 

Assuming those are the only entries in the affected directory, "sudo chmod 755 *" while in that directory should fix things.

Lloyd B.

---

### Post by gzarkadas on 2010-08-01
If you just changed permissions *_only_* inside /var and not below, then you will have to convert them to these (* chars mask irrelevant info):

```

drwxr-xr-x ** root root  **** ****-**-** **:** backups
drwxr-xr-x ** root root  **** ****-**-** **:** cache
drwxrwxrwt ** root root  **** ****-**-** **:** crash
drwxr-xr-x ** root root  **** ****-**-** **:** games
drwxr-xr-x ** root root  **** ****-**-** **:** lib
drwxrwsr-x ** root staff  **** ****-**-** **:** local
drwxrwxrwt ** root root  **** ****-**-** **:** lock
drwxr-xr-x ** root root  **** ****-**-** **:** log
drwxrwsr-x ** root mail  **** ****-**-** **:** mail
drwxr-xr-x ** root root  **** ****-**-** **:** opt
drwxr-xr-x ** root root  **** ****-**-** **:** run
drwxr-xr-x ** root root  **** ****-**-** **:** spool
drwxrwxrwt ** root root  **** ****-**-** **:** tmp

```If you have gone deeper (bu using the -R switch in chmod), then your system will need stronger "medication" than this. Please report your exact situation in the later case.

---

