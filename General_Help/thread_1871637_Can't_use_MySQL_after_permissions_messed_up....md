---
title: "Can't use MySQL after permissions messed up..."
date: 2011-10-29
forum: General Help
---

### Post by Raptor Ramjet on 2011-10-29
Hello,

Yesterday morning I was trying to fix a problem on my mythtv box as when you used the "list videos" function it would hang for a long time (several minutes) with a "video dialog loading or or no videos available" message before mythfrontend crashed and was restarted.

Having looked into things I eventually found a directory in "/var/lib/mythtv/videos" which had no permissions on it ("???????" instead of something like "drwxrw-rw-") so I decided to change the directories owner to "mythtv:mythtv".  

However... I was distracted whilst I was typing so somewhow managed to set a "chown mythtv:mythtv" command going on my root directory and, despite catching this immediately and using "Ctrl-C", this screwed up the ownership of large parts of my system.

So... I swore for a while after which I referred to another working system and after a lot of effort have got the system back up and running with one exception - namely that I can't use anything which requires MySQL (so mythtv, phpmyadmin, etc. can't run)

n.b. The directory and file permissions have not been altered I just had to restore "root:root" to be the owner of most things.

The main symptoms is that when I try to log into MySQL from the command line I get the following:

```

user@machine:~$ mysql -u root -p
Enter password: (not shown but entered correctly !)
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

user@machine:~$ mysql -u mysql -p
Enter password: (not shown but entered correctly !)
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


```

n.b. I am 100% certain that the passwords I am using for "root" and "mythtv" are correct as obviously both these MySQL users were working fine until I screwed up my permissions yesterday morning.

I therefore suspect that the problem is "simply" that I've got the wrong permissions on either a directory or something like a lock file (not sure how MySQL works so this is a guess)

The permissions I have are on what I think are the relevant directories/files are as follows:

```

user@machine:~ sudo ls /var/lib/mysql/ -l
total 20572
-rw-r--r-- 1 mysql mysql        0 2011-05-04 19:51 debian-5.1.flag
-rw-rw---- 1 mysql mysql 10485760 2011-10-29 09:48 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2011-10-29 09:48 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2011-02-05 17:02 ib_logfile1
drwx------ 2 mysql mysql     4096 2011-05-04 19:52 mysql
-rw-rw---- 1 mysql mysql        6 2011-05-04 19:52 mysql_upgrade_info
drwx------ 2 mysql mysql    12288 2011-10-28 16:36 mythconverg
-rw-rw---- 1 mysql mysql        5 2011-10-29 09:48 mythic.pid
drwx------ 2 mysql mysql     4096 2011-02-08 23:44 phpmyadmin

user@machine:~
ls /var/run/mysqld/ -l
total 0
srwxrwxrwx 1 mysql mysql 0 2011-10-29 10:31 mysqld.sock

```

I have also looked at large numbers of forum messages relating to resetting your MySQL passwords but I do not think this will solve my problem.

Finally I realise that it would be easiest to simply reinstall from scratch (which I could do as I'm not really bothered about anything I've recorded with the machine) but if possible I would like to get it running - as a learning exercise if nothing else.

So any help will be most appreciated.

Thank you.

---

### Post by enkay009 on 2011-10-29
Check who mysqld is supposed to be running as. It should be in your /etc/mysql/my.cnf

Also check the error log to see if there were any funny messages when you tried to start mysql. Filesystem permissions errors would be printed here. You'll find the path in your my.cnf.

---

### Post by Raptor Ramjet on 2011-10-29
Firstly thanks for the speedy reply.

And since writing my post I did some more digging about and found there were lots of files and directories in "/tmp/" which were still owned by "mythtv".  After deleting all these and rebooting I was then able to log into MySQL again.

So whilst I'm not exactly sure why this would cause a problem logging into MySQL the main problem has been resolved.

However I now have the problem that several of the tables in my mythconverg database are corrupt so I'll have to see how I can fix this.  

Thanks again for the reply.

---

