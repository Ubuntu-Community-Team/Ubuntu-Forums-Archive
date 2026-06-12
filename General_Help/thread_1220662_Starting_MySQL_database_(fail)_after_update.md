---
title: "Starting MySQL database (fail) after update"
date: 2009-07-23
forum: General Help
---

### Post by Nikol@ on 2009-07-23
Help, i was installed newest updates for ubuntu 9, and my MySQL server on localhost is not working...
I allways started and stoped & restarted MySQL with this 3 commands:
```
/etc/init.d/mysql start
``````
/etc/init.d/mysql stop

``````
/etc/init.d/mysql restart
```And now... now nothing is working...
I just got this error:
```
 * Starting MySQL database server mysqld                                 [fail]
```No error, nothing..
Help please?
I'm beginer in ubuntu, and i don't know much things...
How to fix this?

Thanks :(

---

### Post by Nikol@ on 2009-07-23
bump, anyone? :(

---

### Post by nikgare on 2009-07-23
Please wait more than a few minutes before you try to bump a question.
The usual length is about 24 hours.
Have you looked in the logs?

---

### Post by Nikol@ on 2009-07-23
I'm beginer in linux .. i don't know where is logs from MySQL :(

---

### Post by NoReflex on 2009-07-23
Hello!

As far as I know on debian mysql logs go to syslog - so you might want to check out /var/log/syslog.

Best wishes,
NoReflex

---

### Post by Nikol@ on 2009-07-23
I got this in log:
```
Jul 23 11:50:28 X-desktop /etc/init.d/mysql[17455]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jul 23 11:50:28 X-desktop /etc/init.d/mysql[17455]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jul 23 11:50:28 X-desktop /etc/init.d/mysql[17455]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jul 23 11:50:28 X-desktop /etc/init.d/mysql[17455]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

And i don't understand anything from this errors :confused:

---

### Post by NoReflex on 2009-07-23
From what I see the errors were generated when you tried to restart mysql.
To be sure where mysql stores the log (because this location can be changed) please check the file /etc/mysql/my.cnf
In that file you should find exactly where msyql saves the log.
You could also try to look through the archives of syslog. These files are located in /var/log and have names like syslog.**x**.gz where **x** is a number.

Good luck!

Best wishes,
NoReflex

---

### Post by Nikol@ on 2009-07-23
I finaly solved problem :)
The problem was, i created new pppoe connection (in network manager) and before that i was connecting to the internet with sudo pon-dsl provider...
And that was a problem (i dont know how can that ** up MySQL, but when i connected to the internet with pon command, and restarted again. It's working :)

Ty ppl for help :)

---

