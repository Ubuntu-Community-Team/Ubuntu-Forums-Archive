---
title: "mysql failed to start"
date: 2011-05-06
forum: General Help
---

### Post by romy.mathew on 2011-05-06
when I use 'mysql' in the terminal mysql failed to open with an error 

[COLOR="Red"]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/COLOR]

I did googled and tried various solution but nothing worked for me 
When I tried to restart or start the mysql by 

sudo service mysql start I get following error

[COLOR="red"]start: Rejected send message, 1 matched rules; type="method_call", sender=":1.84" (uid=1000 pid=6865 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))[/COLOR]

At last removed and resinstalled the Mysql but after that the same problem still exist and further I dont even find my.cnf file in /etc/mysql/

Need a help .......

---

### Post by romy.mathew on 2011-05-07
Hi 

I hope this might help someone 

I was getting the error 

[COLOR="Red"]cant-connect-to-local-mysql-server-through-socket-var-lib-mysql-mysql-sock[/COLOR]

I googled almost for 24 hours and found this is common for many users and found some trick work for some but not for all, So I bookmarked all tricks that worked for some and I tried 1 by 1 and finally 1 trick worked for me tooo ..:)

so I am posting all the bookmarks that I did Hope it will work for some one too

1.[http://forums.mysql.com/read.php?11,9689,16123#msg-16123](http://forums.mysql.com/read.php?11,9689,16123#msg-16123)
2.[http://forums.mysql.com/read.php?11,9689,131127#msg-131127](http://forums.mysql.com/read.php?11,9689,131127#msg-131127)
3.[http://forums.mysql.com/read.php?11,9689,131127#msg-131127](http://forums.mysql.com/read.php?11,9689,131127#msg-131127)
4.[http://forums.mysql.com/read.php?11,9689,16554#msg-16554](http://forums.mysql.com/read.php?11,9689,16554#msg-16554)
5.[http://forums.mysql.com/read.php?11,9689,71099#msg-71099](http://forums.mysql.com/read.php?11,9689,71099#msg-71099)
6.[http://forums.mysql.com/read.php?11,9689,90829#msg-90829](http://forums.mysql.com/read.php?11,9689,90829#msg-90829)
7.[http://forums.mysql.com/read.php?11,9689,133717#msg-133717](http://forums.mysql.com/read.php?11,9689,133717#msg-133717)
8.[http://forums.mysql.com/read.php?11,9689,133722#msg-133722](http://forums.mysql.com/read.php?11,9689,133722#msg-133722)
9.[http://forums.mysql.com/read.php?11,9689,143831#msg-143831](http://forums.mysql.com/read.php?11,9689,143831#msg-143831)
10.[http://forums.mysql.com/read.php?11,9689,134374#msg-134374](http://forums.mysql.com/read.php?11,9689,134374#msg-134374)
11.[http://forums.mysql.com/read.php?11,9689,177083#msg-177083](http://forums.mysql.com/read.php?11,9689,177083#msg-177083)
12.[http://forums.mysql.com/read.php?11,9689,178357#msg-178357](http://forums.mysql.com/read.php?11,9689,178357#msg-178357)
13.[http://forums.mysql.com/read.php?11,9689,217503#msg-217503](http://forums.mysql.com/read.php?11,9689,217503#msg-217503)


and This one worked for me 

14. mysqld_safe --skip-grant-tables --skip-networking &

after this solution I moved into mysql and was able to go on smoothly.

---

