---
title: "Can't connect to local MySQL server through socket"
date: 2010-07-09
forum: General Help
---

### Post by mrjavoman on 2010-07-09
*UPDATE I found the problem*

the problem is that i wrote mysqld.socket instead of mysqld.sock on the my.cnf file when setting up the my.cnf file
it was a lousy mistake.

i just renamed mysqld.socket to mysqld.sock as the error suggested and it worked, it just so happens that when i ran it from it's directory it was working which is what threw me off.


hello  I've compiled mysql server version 5.0.77 and so far everything seems working ok but I am having problems when I try to run mysql I get this error:
```

xavi@VirtualUbuntuServer:~$ mysql -u root -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

but if i run it from its directory it does work:
```
xavi@VirtualUbuntuServer:~$ /usr/local/mysql/bin/mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.0.77-log Source distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

```

here is my path variable
```
xavi@VirtualUbuntuServer:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/mysql/bin

```

the socket is on /var/run/mysqld and the here is the permissions
```
xavi@VirtualUbuntuServer:~$ ls -la /var/run/mysqld/
total 0
drwxr-xr-x  2 mysql root   60 2010-07-09 09:37 .
drwxr-xr-x 21 root  root  680 2010-07-09 09:41 ..
srwxrwxrwx  1 mysql mysql   0 2010-07-09 09:37 mysqld.socket

```
and mysql is running 
```
xavi@VirtualUbuntuServer:~$ ps -A | grep mysql
  859 ?        00:00:00 mysqld_safe
  889 ?        00:00:00 mysqld

```

I would appreciate if anyone could help me figure this, problem from what I've read it seems it might be a permission problem but I haven't been able to figure it out 

thanks.

---

