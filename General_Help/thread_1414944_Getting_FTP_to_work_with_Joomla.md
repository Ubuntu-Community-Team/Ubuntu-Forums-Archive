---
title: "Getting FTP to work with Joomla"
date: 2010-02-24
forum: General Help
---

### Post by auraithx on 2010-02-24
I've been on the #ubuntu IRC for hours trying to figure this out. Here are some outputs of relevant commands.

ls -ltr /var/
```

total 40
drwxrwsr-x  2 root     staff    4096 Oct 20 00:04 local
drwxr-xr-x  2 root     root     4096 Oct 30 17:57 opt
drwxrwxrwx 11 root     root     4096 Jan 25 11:02 cache
drwxrwxrwt  2 root     root     4096 Jan 25 15:47 tmp
drwxr-xr-x  7 root     root     4096 Feb  1 10:49 spool
drwxr-xr-x 37 root     root     4096 Feb  1 10:49 lib
drwxr-xr-x  2 root     root     4096 Feb 16 06:25 backups
drwxrwsr-x 11 ftpuser3 www-data 4096 Feb 24 12:09 www
drwxrwsrwt  2 root     mail     4096 Feb 24 13:21 mail
drwxrwxrwx 14 root     root     4096 Feb 24 13:31 log
drwxrwxrwt  3 root     root       60 Feb 24 13:32 lock
drwxr-xr-x 11 root     root      480 Feb 24 13:32 run


```

cat /etc/passwd|grep ftpuser
```

ftpuser3:x:1003:1003::/var/www/:/bin/bash
```

id ftpuser3
```
uid=1003(ftpuser3) gid=1003(ftpuser3) groups=1003(ftpuser3),33(www-data)
```


I can log in via FTP absolutely fine, I cannot CHMOD files or upload files though. 

Any help is **severely **appreciated.

---

### Post by auraithx on 2010-02-24
I just followed this tutorial ([http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)) 

and set up a entirely different user using proftp, still when trying to CHMOD files I get this error

```

Command:	SITE CHMOD 775 webpics
Response:	550 CHMOD 775 webpics: Operation not permitted
```

---

### Post by auraithx on 2010-02-24
Okay, I completely uninstalled vsftp and proftpd and reinstalled vsftp.

Deleted all the users I was working with.

Created a new user 'joomla' Set /var/www as his home directory
```
cat /etc/passwd|grep joomla
joomla:x:1004:1004::/var/www:/bin/sh

```
Added him to the www-data group
```
id joomla
uid=1004(joomla) gid=1004(joomla) groups=1004(joomla),33(www-data)

```

Gave the www-data group full write permission
```
ls -ltr /var/
total 40
drwxrwsr-x  2 root     staff    4096 Oct 20 00:04 local
drwxr-xr-x  2 root     root     4096 Oct 30 17:57 opt
drwxrwxrwx 11 root     root     4096 Jan 25 11:02 cache
drwxrwxrwt  2 root     root     4096 Jan 25 15:47 tmp
drwxr-xr-x  7 root     root     4096 Feb  1 10:49 spool
drwxr-xr-x 37 root     root     4096 Feb  1 10:49 lib
drwxr-xr-x  2 root     root     4096 Feb 16 06:25 backups
drwxrwxrwx 15 root     root     4096 Feb 24 14:29 log
drwxrwxrwt  3 root     root       80 Feb 24 16:16 lock
drwxrwsrwt  2 root     mail     4096 Feb 24 16:18 mail
drwxr-xr-x 12 root     root      500 Feb 24 16:18 run
drwxrwsr-x 11 ftpuser3 www-data 4096 Feb 24 16:34 www

```

Connect via FTP with FileZilla.

I can connect fine.
I can rename files.
I can upload NEW files.
I cannot edit existing files.
I cannot change the CHMOD of files.

:confused::confused::confused:

---

### Post by auraithx on 2010-02-24
I fixed this with the command 

chown -R joomla /var/www 

which sets the user 'joomla' as owner of all directories/files inside /var/www - so I assume there is a major downside to doing this.

But I've been trying to fix this for 2 days now so any fix will do. If anyone knows a more secure method I'd love to hear it. :popcorn: (I assume this can be achieved with the newgrp command?)

---

