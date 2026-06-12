---
title: "Munged permission in /var"
date: 2012-02-14
forum: General Help
---

### Post by babajc on 2012-02-14
I just found that another server admin ran the following command while in /var:
find -type d -print0 | xargs -0 chmod 0775

Now, much is broke.  Any advice on how to recover?

Thanks.

---

### Post by josephmills on 2012-02-14
dang xargs 
please tell him/her/person that plays with Find 
to read this 
6. Actions in bulk: xargs, -print0 and -exec +
[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)


could we please see the permissions of var now ? 
```
ls -al /var/ 
```
thanks

---

### Post by babajc on 2012-02-14
Will point them that way. :)

Here's the current permissions:
```
root@noviolation:/var# ls -al /var/
total 108
drwxr-xr-x 23 root     root      4096 2012-02-14 10:02 .
drwxr-xr-x 23 root     root      4096 2012-02-14 09:39 ..
drwxr-xr-x  3 root     root      4096 2012-02-14 10:14 backups
drwxr-xr-x 14 root     root      4096 2011-02-10 14:10 cache
drwxrwxr-x 20 root     root      4096 2010-11-30 08:53 chroot
drwxr-xr-x 19 root     www-data  4096 2012-02-10 09:50 crm
drwxrwxr-x  2 root     webdev    4096 2010-12-16 11:25 dev
drwxrwxr-x 14 root     root      4096 2011-06-20 15:30 joomla15_backup
drwxr-xr-x 50 root     root      4096 2011-12-21 08:27 lib
drwxrwsr-x  2 root     staff     4096 2010-04-23 03:23 local
drwxrwxrwt  3 root     root        60 2012-02-14 10:14 lock
drwxr-xr-x 19 root     root      4096 2012-02-14 10:14 log
drwxrwsr-x  2 root     man       4096 2011-08-18 12:09 mail
drwxrwxr-x 16 www-data www-data 12288 2010-10-18 10:23 mantis
drwxr-xr-x  2 root     root      4096 2010-04-22 12:09 opt
drwxr-xr-x 13 root     root       560 2012-02-14 10:14 run
drwxr-xr-x  7 root     root      4096 2010-10-22 10:40 spool
drwxrwxr-x  6 root     www-data  4096 2011-10-20 13:28 svn
drwxrwxr-x  6 root     root      4096 2010-11-30 13:26 tmp
drwxrwxr-x  4 www-data www-data  4096 2010-11-23 11:12 trac
drwx------  3 root     bin       4096 2011-08-25 11:48 webmin
drwxrwxrwx 59 root     www-data 20480 2012-02-14 06:11 www
drwxrwxr-x  2 root     root      4096 2011-08-25 10:46 www-ssl
```
Thanks!

---

### Post by josephmills on 2012-02-14
Here is what I have for one of my servers If you would like to match up 
```
drwxr-xr-x 15 root     root     4096 2012-01-31 18:25 .
drwxr-xr-x 23 root     root     4096 2012-02-13 06:33 ..
drwxr-xr-x  2 root     root     4096 2012-02-14 06:28 backups
drwxr-xr-x 11 root     root     4096 2012-01-27 06:25 cache
drwxrwxrwt  2 root     root     4096 2012-02-08 14:24 crash
drwxr-xr-x 39 root     root     4096 2012-02-08 15:19 lib
drwxrwsr-x  2 root     staff    4096 2011-10-09 03:31 local
lrwxrwxrwx  1 root     root        9 2012-01-17 20:11 lock -> /run/lock
drwxr-xr-x 12 root     root     4096 2012-02-14 06:28 log
drwxrwsr-x  2 root     mail     4096 2012-01-17 20:11 mail
drwxr-xr-x  2 root     root     4096 2012-01-17 20:11 opt
lrwxrwxrwx  1 root     root        4 2012-01-18 01:19 run -> /run
drwxr-xr-x  4 root     root     4096 2012-01-17 20:13 spool
drwxrwxrwt  2 root     root     4096 2012-02-08 13:29 tmp
drwxr-xr-x  2 root     bin      4096 2012-02-01 14:26 usermin
drwx------  3 root     bin      4096 2012-02-08 15:11 webmin
drwxr-sr-x  2 www-data www-data 4096 2012-01-30 19:51 www

```

so it dont look that bad !

---

### Post by babajc on 2012-02-14
Looks better than I thought!

Thanks!

---

