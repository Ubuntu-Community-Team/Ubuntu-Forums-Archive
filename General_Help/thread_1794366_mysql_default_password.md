---
title: "mysql default password"
date: 2011-06-30
forum: General Help
---

### Post by nethero on 2011-06-30
Just installed mysql and was wondering if there is a default password.  When I type....

```
mysql -h localhost -u mylinuxusername -p
Enter password:  *******
```

I get...

```
ERROR 1045 (28000): Access denied for user ' mylinuxusername'@'localhost' (using password: YES)
```

In the past I would have typed...
```

mysql -u root mysql
```

but this also gives me the same error message.

---

### Post by raja.genupula on 2011-06-30
hey man 
 have you started the service of the mysql 
 ```
sudo /etc/init.d/mysql start
```


just do this 
and do what ever you did above

---

### Post by Habitual on 2011-06-30
Installing mysql doesn't mean you have a *mysql-server *installed btw....

---

### Post by nethero on 2011-07-01
> **Habitual said:**
> Installing mysql doesn't mean you have a *mysql-server *installed btw....

I have the following packages installed....
mysql-client
mysql-server
mysql-admin
mysql-common
mysql-query browser

[QUOTE=raja.genupula]hey man 
 have you started the service of the mysql [/QUOTE]

I ran the code and received this message...

[I]Rather than invoking init scripts through /etc/init.d, use the service(8 )
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8 ) utility, e.g. start mysql[/I]

I ran "start mysql" and got this message....

*start: Rejected send message, 1 matched rules; type="method_call", sender=":1.49" (uid=1000 pid=2585 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))*

---

### Post by Habitual on 2011-07-01
and ```
sudo service mysql start
``` does or doesn't start mysql server?

Open a terminal and type
```
pidof mysqld
``` to find out.

Did you "set" a root user password during install? (a GUI'ish dialog should have been presented).

If you did or don't remember you can find it out by
```
sudo apt-get install -y debconf-utils
sudo debconf-get-selections | grep mysql| grep root
```

Please let us know...

---

### Post by nethero on 2011-07-01
Thanks for the help.  I ran the commands you suggested

```
sudo service mysql start
```This returns:   "start: Job is already running: mysql"

```
pidof mysqld
```This returns:   "1131"


I don't think I did set a password.  I installed debconf-utils and ran the debconf-get-selections command and it returned...

```
mysql-server-5.1    mysql-server/root_password_again    password    
mysql-server-5.1    mysql-server/root_password    password    
```So I guess the default password is "password".  I tried running...

```
mysql -h localhost -u root -p
```and I still got the error "Access denied for user 'root'@'localhost' (using password: YES)"

---

### Post by nethero on 2011-07-01
Habitual,

Thanks for your help, I was able to resolve my problem.  I went to[ here to reset my root password]("http://dev.mysql.com/doc/refman/5.1/en/resetting-permissions.html").  This proved troublesome at first because I couldn't kill mysqld even using "sudo killall mysqld".  However, I forgot that Ubuntu has upstart restarting mysqld everytime I tried to kill it so I renamed /etc/init/mysql.conf to /etc/init/mysql.conf.bak and restarted my computer.   Then I was successfully able to reset my password.  Now when I type "mysql -h localhost -u root -p and enter my new password I get the mysql prompt.

---

### Post by Habitual on 2011-07-02
+1 for fixing it yourself.

Always glad to be of assistance.

---

