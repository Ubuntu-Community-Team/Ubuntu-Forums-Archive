---
title: "can't reset root password for mysql on ubuntu 3.2"
date: 2012-08-16
forum: General Help
---

### Post by cpama on 2012-08-16
I'm just new to mysql so I apologize for any silly questions. 
My problem started off with me not being able to log in as root anymore into my mysql install.  I was attempting to run mysql without passwords turned on... but whenever I would run the command : 

```
        # mysqld_safe --skip-grant-tables &
```I would never get a prompt back... (I was trying to follow the instructions here: [http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html))
The screen just looks like this: 
```

     root@jj-SFF-PC:/usr/bin# mysqld_safe --skip-grant-tables
     120816 11:40:53 mysqld_safe Logging to syslog.
     120816 11:40:53 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

```and i don't get a prompt to start typing the sql commands to reset the password. 

when i kill it by doing a ctrl-c, i get the following message: 

```
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```If I retry the command and leave it long enough, I do get the following series of messages:

```
        root@jj-SFF-PC:/run/mysqld# 120816 13:15:02 mysqld_safe Logging to syslog.
120816 13:15:02 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
120816 13:16:42 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
 
[1]+  Done                    mysqld_safe --skip-grant-tables
root@jj-SFF-PC:/run/mysqld# 
```But then if i try to log in as root by doing: 

   ```
   # mysql -u root
```I get the following error message: 

```
        ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```I checked and /var/run/mysqld/mysqld.sock file doesn't not exist. The folder does, but not the file.  
Also, I dunno if this helps or not, but I found did a "find / -name mysqld" and it came up with:

```
     /var/run/mysqld - folder
     /usr/sbin/mysqld - file
     /run/mysqld - folder
```I'm just new to linux and mysql, so i don't know if this is normal or not. But I'm including this info just in case it helps ...

any suggestions?  I'm running on ubuntu.

---

### Post by Wim Sturkenboom on 2012-08-16
Your mysql daemon is not running, that's why you get the 'Error 2002'; if you look in one of the earlier codeblocks that you posted, it states that it's ended. 

You simply do not always get a prompt back when you 'push' a program to the background till you press <enter>, regardless if the command is successful or not.

You can try the solution in post #4 in [http://ubuntuforums.org/showthread.php?t=1836919](http://ubuntuforums.org/showthread.php?t=1836919) It's probably the quickest way; also read post #2 for possible mysql statements to reset the password.

PS
Don't follow random instructions from the web; follow specific instructions for Ubuntu.

---

### Post by cpama on 2012-08-16
> **Wim Sturkenboom said:**
> Your mysql daemon is not running, that's why you get the 'Error 2002'; if you look in one of the earlier codeblocks that you posted, it states that it's ended. 

You simply do not always get a prompt back when you 'push' a program to the background till you press <enter>, regardless if the command is successful or not.

You can try the solution in post #4 in [http://ubuntuforums.org/showthread.php?t=1836919](http://ubuntuforums.org/showthread.php?t=1836919) It's probably the quickest way; also read post #2 for possible mysql statements to reset the password.

PS
Don't follow random instructions from the web; follow specific instructions for Ubuntu.

Thanks for the response Wim.  I've tried post #2, i get the following message: 

InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld

and it just keeps going...

---

### Post by cpama on 2012-08-16
> **Wim Sturkenboom said:**
> Your mysql daemon is not running, that's why you get the 'Error 2002'; if you look in one of the earlier codeblocks that you posted, it states that it's ended. 

You simply do not always get a prompt back when you 'push' a program to the background till you press <enter>, regardless if the command is successful or not.

You can try the solution in post #4 in [http://ubuntuforums.org/showthread.php?t=1836919](http://ubuntuforums.org/showthread.php?t=1836919) It's probably the quickest way; also read post #2 for possible mysql statements to reset the password.

PS
Don't follow random instructions from the web; follow specific instructions for Ubuntu.

Thanks for the response Wim.  I've tried post #2, i get the following message: 

InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld

and it just keeps going...

i wasn't sure where this ibdata1 was located so i tried to do a find on it but i was getting a huge list of files with "permission denied" next to it. 

i did find the following in my /var/lib/mysql folder: 


ls -l /var/lib/mysql
total 45080
-rwxrwxrwx 1 root  root         0 Aug 10 15:25 debian-5.5.flag
-rwxrwxrwx 1 mysql mysql 35651584 Aug 16 08:50 ibdata1
-rwxrwxrwx 1 mysql mysql  5242880 Aug 16 08:50 ib_logfile0
-rwxrwxrwx 1 mysql mysql  5242880 Aug 14 09:46 ib_logfile1
drwxrwxrwx 2 mysql root      4096 Aug 10 15:26 mysql
-rwxrwxrwx 1 root  root         6 Aug 10 15:26 mysql_upgrade_info
drwxrwxrwx 2 mysql mysql     4096 Aug 10 15:25 performance_schema
drwxrwxrwx 2 mysql mysql     4096 Aug 10 15:28 phpmyadmin
drwxrwxrwx 2 mysql mysql     4096 Aug 14 09:50 racktables
drwxrwxrwx 2 mysql root      4096 Aug 10 15:25 test

---

### Post by Wim Sturkenboom on 2012-08-16
You start with post #4 and login to the mysql server using the debian-sys-maint user (normal mysql server running, no need for something special).

Post #2 was only referred to for the commands *_update user set password=password('yourpassword') where user='root'_* and *_grant all privileges on *.* to 'root'@'localhost' identified by 'yourpassword' with grant option_*

---

### Post by cpama on 2012-08-16
> **Wim Sturkenboom said:**
> You start with post #4 and login to the mysql server using the debian-sys-maint user (normal mysql server running, no need for something special).

Post #2 was only referred to for the commands *_update user set password=password('yourpassword') where user='root'_* and *_grant all privileges on *.* to 'root'@'localhost' identified by 'yourpassword' with grant option_*

Wim, i don't know the password for  debian-sys-maint user.  The guy who installed this mysql database says he set it up as a certain value, but its not working
=(

Should i just reinstall mysql?

---

### Post by Wim Sturkenboom on 2012-08-17
> **cpama said:**
> Wim, i don't know the password for  debian-sys-maint user.  The guy who installed this mysql database says he set it up as a certain value, but its not working
=(

Should i just reinstall mysql?

Don't you know the password or does it not work? The password for debian-sys-maint is in the file *_/etc/mysql/debian.cnf_* (as said in post #4 in the other thread). If it does not exist in there, the Ubuntu update manager might not be able to configure mysql when updating it.

The only reason why it would not work with debian-sys-maint is if somebody fiddled with that mysql account (removed it or changed password).

If you really can't get in, a re-install is the only option (to my knowledge).

Good luck.

PS

Make a binary backup (copy files) from everything in /var/lib/mysql. You might need it later to restore.

---

