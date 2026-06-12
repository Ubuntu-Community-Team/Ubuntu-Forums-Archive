---
title: "MySql"
date: 2012-02-10
forum: General Help
---

### Post by lonewolf69 on 2012-02-10
I moved my server to a different building and most seems ok.  I use webmin to administer the machine and checked MYSQL and it is not running.  I get this message:

----------------------------------------------------------------------------------------------------------------------------------
Click this button to start the MySQL database server on your system with the command /etc/init.d/mysql start >/dev/null 2>&1 &. This Webmin module cannot administer the database until it is started.

And there is a button to the left "Start MySql Server"
----------------------------------------------------------------------------------------------------------------------------------

Nothing happens when I click it.  

I then went to the server and manually tried to start the service and nothing happened.

Does anyone have any ideas?  There really is not anything on it and I could simply remove and reinstall but I would like to figure out what the issue is.

Thanks.
K

---

### Post by The Cog on 2012-02-11
What does it say if you try this command on the command line?
> sudo /etc/init.d/mysql start
Two things come to mind:
* maybe it's mysqld or mysql-server rather than just mysql (I can't remember right now)
* with recent Ubuntus, maybe **sudo start mysql** would be better

I can't think of any reason why moving the machine might prevent mysql starting.

---

### Post by lonewolf69 on 2012-02-17
OK,..I got...

"Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service mysql start"

"Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start mysql mysql start/running"

It is very weird, webmin is showing that it is not running when I click on "Servers/Mysql Database Server."

When I click on Bootup and Shutdown it says "Yes/Yes" for "Start At Boot" and "Running Now"

I am not sure what to make of this. If it is running why can't I administer through Webmin, and if it is not running why is it saying on the other page it is?  What is an Upstart Service?  I just want to get back to work here.

---

### Post by Leppie on 2012-02-17
try something like this:
```
mysql -h localhost -u root -p
```
if you can login, mysql is running.

---

### Post by lonewolf69 on 2012-02-18
I get ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Does this mean it is not running?

---

### Post by Leppie on 2012-02-18
It seems like that. Could you post the output of the following command:
```
ps -ef | grep mysql
```

---

### Post by SeijiSensei on 2012-02-18
> **lonewolf69 said:**
> "Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service mysql start"

"Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start mysql mysql start/running"

What is an Upstart Service?  I just want to get back to work here.

Ubuntu has been converting servers from the older /etc/init.d/ script method to its newer "upstart" service manager.  To start your MySQL server run the command "sudo service mysql start".

Probably the MySQL module in your version of Webmin hasn't been updated to handle the new method for service management.  You can try installing the [.deb available at the Webmin site]("http://prdownloads.sourceforge.net/webadmin/webmin_1.580_all.deb") and see if that resolves the problem.  Download the .deb file, then install it with "sudo dpkg -i webmin_1.580_all.deb".

---

### Post by lonewolf69 on 2012-02-18
ps -ef | grep mysql  = "1000    12334  1689   0 10:06 ttyl     00:00:00 grep --color=auto mysql"

sudo /etc/init.d/mysql start = "start: Job is already running: mysql"


I installed the new webmin and still get the same message.

---

### Post by Leppie on 2012-02-18
> **lonewolf69 said:**
> ```
ps -ef | grep mysql 
1000    12334  1689   0 10:06 ttyl     00:00:00 grep --color=auto mysql
```
this indicates mysql is not running.

which version of mysql do you have installed, and which server os are you running?

---

### Post by Iowan on 2012-02-18
> **Leppie said:**
> It seems like that. Could you post the output of the following command:
```
ps -ef | grep mysql
```
That didn't work on my machine, although **sudo ps -ef | grep mysql** did...

---

### Post by lonewolf69 on 2012-02-18
I reran the "ps -ef|grep mysql" and got nearly the same result except for time of course and the second set of numbers was 13546.

I am using 11.04.  And the mysql is 5.X (not sure exactly which one).

---

### Post by lonewolf69 on 2012-02-18
I reran the "ps -ef|grep mysql" and got nearly the same result except  for time of course and the second set of numbers was 13546.

I am using 11.04.  And the mysql is 5.X (not sure exactly which one).

---

### Post by Leppie on 2012-02-18
> **Iowan said:**
> That didn't work on my machine, although **sudo ps -ef | grep mysql** did...
then it may also be worth trying to login with sudo:
```
sudo mysql -h localhost -u root -p
```

---

### Post by lonewolf69 on 2012-02-18
"mysql -h localhost -u root -p" returned "ERROR 2002 (HY000_: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by Leppie on 2012-02-18
> **lonewolf69 said:**
> "mysql -h localhost -u root -p" returned "ERROR 2002 (HY000_: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
and ```
sudo mysql -h localhost -u root -p
```?

---

### Post by lonewolf69 on 2012-02-18
I did have the "sudo" in front.  My bad in the repost

---

### Post by Leppie on 2012-02-18
could you post the output of the following command, like Iowan suggested:
```
sudo ps -ef | grep mysql
```

---

### Post by lonewolf69 on 2012-02-18
>sudo ps -ef|grep mysql 

>1000   16021 1689 0 16:29 tty1    00:00:00 grep --color=auto mysql

---

### Post by Iowan on 2012-02-18
Probably a silly question, but you ARE running this on the server itself?

---

### Post by lonewolf69 on 2012-02-19
Yes I am.  I am trying to use webmin to administer it from another machine.  All the terminal posts are from the server, and the webmin posts are from the workstation.

---

### Post by Iowan on 2012-02-19
> **lonewolf69 said:**
> "mysql -h localhost -u root -p" returned "ERROR 2002 (HY000_: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)The socket error has me confused - wish I knew more about 'em.
Found [this]("http://ubuntuforums.org/showthread.php?t=1689258") similar thread, but it doesn't look like a solution.
[Another]("http://ubuntuforums.org/showthread.php?t=1601420") that doesn't look like a pleasant solution - except the last post is promising.

---

