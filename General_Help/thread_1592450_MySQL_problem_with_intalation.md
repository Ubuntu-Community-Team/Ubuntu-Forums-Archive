---
title: "MySQL problem with intalation"
date: 2010-10-10
forum: General Help
---

### Post by etherlord on 2010-10-10
Hello I have problem with install MySQL package mysql-5.1.51-linux-i686-glibc23.tar.gz. I unpack it and I do that :
```

root@etherlord-laptop:/home/etherlord# cd /usr/local
root@etherlord-laptop:/usr/local# ls -l
total 36
drwxr-xr-x  2 mysql mysql 4096 2010-08-16 11:32 bin
drwxr-xr-x  2 mysql mysql 4096 2010-08-16 11:32 etc
drwxr-xr-x  2 mysql mysql 4096 2010-08-16 11:32 games
drwxr-xr-x  2 mysql mysql 4096 2010-08-16 11:32 include
drwxr-xr-x  4 mysql mysql 4096 2010-10-05 19:24 lib
lrwxrwxrwx  1 mysql mysql    9 2010-10-05 00:24 man -> share/man
lrwxrwxrwx  1 root  root    31 2010-10-10 11:29 mysql -> mysql-5.1.51-linux-i686-glibc23
drwxr-xr-x 13 mysql mysql 4096 2010-09-13 18:15 mysql-5.1.51-linux-i686-glibc23
drwxr-xr-x  2 mysql mysql 4096 2010-08-16 11:32 sbin
drwxr-xr-x  8 mysql mysql 4096 2010-08-16 11:46 share
drwxr-xr-x  2 mysql mysql 4096 2010-08-16 11:32 src
root@etherlord-laptop:/usr/local# ln -s mysql-5.1.51-linux-i686-glibc23 mysql
root@etherlord-laptop:/usr/local# cd mysql
root@etherlord-laptop:/usr/local/mysql# chmod u+rwx
chmod: missing operand after `u+rwx'
Try `chmod --help' for more information.
root@etherlord-laptop:/usr/local/mysql# chmod u+rwx mysql
chmod: cannot access `mysql': No such file or directory
root@etherlord-laptop:/usr/local/mysql# groupadd mysql
groupadd: group 'mysql' already exists
root@etherlord-laptop:/usr/local/mysql# useradd -g  mysql msql
root@etherlord-laptop:/usr/local/mysql# chown -R mysql .
root@etherlord-laptop:/usr/local/mysql# chgrp -R mysql .
root@etherlord-laptop:/usr/local/mysql# ls -l
total 152
drwxr-xr-x  2 mysql mysql  4096 2010-09-13 18:15 bin
-rw-r--r--  1 mysql mysql 17987 2010-09-13 18:15 COPYING
drwxr-x---  4 mysql mysql  4096 2010-09-13 18:15 data
drwxr-xr-x  2 mysql mysql  4096 2010-09-13 18:15 docs
-rw-r--r--  1 mysql mysql  5139 2010-09-13 18:15 EXCEPTIONS-CLIENT
drwxr-xr-x  2 mysql mysql  4096 2010-09-13 18:15 include
-rw-r--r--  1 mysql mysql 12741 2010-09-13 18:15 INSTALL-BINARY
drwxr-xr-x  3 mysql mysql  4096 2010-09-13 18:15 lib
drwxr-xr-x  4 mysql mysql  4096 2010-09-13 18:15 man
lrwxrwxrwx  1 mysql mysql    31 2010-10-10 14:17 mysql-5.1.51-linux-i686-glibc23 -> mysql-5.1.51-linux-i686-glibc23
drwxr-xr-x 10 mysql mysql  4096 2010-09-13 18:15 mysql-test
-rw-r--r--  1 mysql mysql 62975 2010-09-13 18:15 README
drwxr-xr-x  2 mysql mysql  4096 2010-09-13 18:15 scripts
drwxr-xr-x 27 mysql mysql  4096 2010-09-13 18:15 share
drwxr-xr-x  5 mysql mysql  4096 2010-09-13 18:15 sql-bench
drwxr-xr-x  2 mysql mysql  4096 2010-09-13 18:15 support-files
root@etherlord-laptop:/usr/local/mysql# scripts/mysql_install_db --user=mysql

FATAL ERROR: Could not find mysqld

The following directories were searched:

    /usr/libexec
    /usr/sbin
    /usr/bin

If you compiled from source, you need to run 'make install' to
copy the software into the correct location ready for operation.

If you are using a binary release, you must either be at the top
level of the extracted archive, or pass the --basedir option
pointing to that location.

```

Could someone help me ??

PS. I need that for study

---

