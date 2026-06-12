---
title: "understanding mysql and mysqld on ubuntu"
date: 2010-12-22
forum: General Help
---

### Post by andrea_bio on 2010-12-22
Hi
 
I'm struggling a bit with mysql on linux. At present i am asking for information/knowledge rather than how to fix the problem i am experiencing. I'm a linux beginner and need to understand more
 
I'm using ubuntu linux 10.10 .
 
1) I believe mysqld is the underlying database server and mysql is a client to connect to mysql. Is this correct?
 
2)How do i find out if mysqld and mysql are running. Should they be 2 separate processes? 
 
 
3) When i look up for how to restart mysql on ubuntu linux on the internet it always says service mysql restart and not service mysqld restart. Why do you restart the client and not the underlying server?
 
4) Does the following error mean mysqld is not running or that it is running and mysql client can't connect to it:
 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
 
 
5) when i look in the ps list of a machine that has mysql installed properly i see this:
mysql      885     1 21 Dec21 ?        04:37:21 /usr/sbin/mysqld

I presume this is the mysqld daemon?
 
6) The following command was ran on a machine where mysql is playing up. What does this ps -ef | grep mysql tell me
ps -ef | grep mysql
root 32154 30101 0 20:14 pts/1 00:00:00 grep --color=auto mysql
 
Is this actually showing me the ps command and, being as there is nothing else in the list, this means mysqld isnt running
 
thanks

---

### Post by lykwydchykyn on 2010-12-22
> **andrea_bio said:**
> Hi
I'm struggling a bit with mysql on linux. At present i am asking for information/knowledge rather than how to fix the problem i am experiencing. I'm a linux beginner and need to understand more
 
I'm using ubuntu linux 10.10 .
 
1) I believe mysqld is the underlying database server and mysql is a client to connect to mysql. Is this correct?
 
yes.
> 
2)How do i find out if mysqld and mysql are running. Should they be 2 separate processes? 

The server should have a process if it is running.  The client only runs when you launch it to log in to mysqld.  You can also run this to see the status of the server:
```

sudo service mysql status

``` 
 > 
3) When i look up for how to restart mysql on ubuntu linux on the internet it always says service mysql restart and not service mysqld restart. Why do you restart the client and not the underlying server?

You are restarting the server.  This is one of those situations where it's been changed to "mysql" to make it easier, but it makes it somewhat more confusing as well.  

>    
4) Does the following error mean mysqld is not running or that it is running and mysql can't connect to it:
 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)


Normally, yes.
 > 
5) What does this ps -ef | grep mysql tell me
ps -ef | grep mysql
root 32154 30101 0 20:14 pts/1 00:00:00 grep --color=auto mysql
 
Is this actually showing me the ps command and, being as there is nothing else in the list, this means mysql isnt running


Looks like that is correct.  If it were running, you'd see a process called 'mysqld'.

---

### Post by Nimbus200 on 2010-12-22
1. Yes, 'd' stands for 'daemon'

2. Yes, they're both two separate things. mysqld is MySQL database server application, while mysql is a client application which the same as its gui counterpart (MySQL Query Browser for example) to connect and do tasks with an instance of MySQL server.

3. mysql here in term of 'service mysql restart' or '/etc/init.d/mysql restart' is just a name of a service. mysqld is the name of the application while mysql is the name of the service / daemon application.

4. Make sure your MySQL database server is up and running. You can check it using : nestat -tapln | grep 3306
Make sure your firewall is not blocking connection to port 3306 ( allow access from localhost to localhost on destination port 3306 )

5. Have no idea...lol

---

