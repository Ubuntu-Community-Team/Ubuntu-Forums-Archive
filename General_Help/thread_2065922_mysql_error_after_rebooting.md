---
title: "mysql error after rebooting"
date: 2012-10-03
forum: General Help
---

### Post by micahpage on 2012-10-03
I had some weird things happen, that i figured needed a reboot.

After I rebooted I went to my forums to find this error msg:
```
MyBB has experienced an internal SQL error and cannot continue.

SQL Error:
2002 - Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Query:
[READ] Unable to connect to MySQL server
```


after this i tried to start/stop/restart mysql server:
```
metulburr@ubuntu:~$ sudo /etc/init.d/mysql restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop mysql ; start mysql. The restart(8) utility is also available.
start: Job failed to start
metulburr@ubuntu:~$ sudo /etc/init.d/mysql stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
metulburr@ubuntu:~$ mysq
No command 'mysq' found, did you mean:
 Command 'mysql' from package 'mysql-client-core-5.5' (main)
mysq: command not found
metulburr@ubuntu:~$ /bin/mysq
bash: /bin/mysq: No such file or directory
metulburr@ubuntu:~$ /bin/mysql
bash: /bin/mysql: No such file or directory
metulburr@ubuntu:~$ sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Job failed to start
metulburr@ubuntu:~$ service mysql start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.68" (uid=1000 pid=4282 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
metulburr@ubuntu:~$ start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.69" (uid=1000 pid=4293 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
metulburr@ubuntu:~$ mysql start
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
metulburr@ubuntu:~$ 

```

I see the error msgs, but not sure what to do about it?

---

### Post by raja.genupula on 2012-10-03
ok try this 
```
sudo  service mysql stop
```

---

### Post by micahpage on 2012-10-03
yeah i did that: i got an error



OK i figured it out. My inet addr changed when i rebooted, and i reset router for port forwards to the correct inet addr, but i didn't know that this file still had the old inet addr in it. which cause a lot of headaches


in file:
```
/etc/mysql/my.cnf

```
i ahd to change to the new inet address:
```
bind-address		= 192.168.1.7
```

---

