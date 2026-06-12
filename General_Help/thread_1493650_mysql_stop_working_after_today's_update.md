---
title: "mysql stop working after today's update"
date: 2010-05-26
forum: General Help
---

### Post by alex_time on 2010-05-26
I'am using ubuntu lucid, after today's system updates, mysql stop working at all. Log file at /var/log/mysql/error.log does not say anything about today, and whe I try to start it the terminal hang also in verbose mode.

What can I check?!

---

### Post by alex_time on 2010-05-26
daemon.log says:


 init: mysql main process (1032) terminated with status 1

---

### Post by alex_time on 2010-05-26
if I lunch mysql with the command 

mysqld 

it starts...

---

### Post by StuartN on 2010-05-26
> **alex_time said:**
> if I lunch mysql with the command

At a guess that sounds like a permissions problem. I did not see any sql components in today's updates.

What was the previous method of launching mysql, the method that failed?

---

### Post by alex_time on 2010-05-26
> **StuartN said:**
> At a guess that sounds like a permissions problem. I did not see any sql components in today's updates.

What was the previous method of launching mysql, the method that failed?

Mysql starts by init.d script automatically, now I removed the init.d link (update-rc.d -f mysql remove) and if I start it with the command

service mysql start
or
start mysql

the command never ends, I have to CTRL+C to stop it. And the mysql error.log does not say anything.

How can I check if it is a permission problem? And if it is, why mysql start with mysqld command?

Apparmor configuration is ok, are there other tools/server checking permission?

---

### Post by alex_time on 2010-05-27
if I start mysql like this

dmesg|mysqld

it starts with no problem, no error messages...what's the difference between start mysql from mysqld command and from "service mysql start"?!

---

### Post by StuartN on 2010-05-27
> **alex_time said:**
> what's the difference between start mysql from mysqld command and from "service mysql start"?!

I think you answered your own question - mysql is different from mysqld

---

### Post by alex_time on 2010-05-27
> **StuartN said:**
> I think you answered your own question - mysql is different from mysqld

yes but...when I run "service mysql start" I am not running mysql client, I am running mysql server like mysqld does, isn't it?! Both are for server, the same mysql server in the same machine. If the problem is about some mysql data files permission, mysqld should not work as "service mysql start" does, what log can I check? the "service" "program" could be the key? How does it work? I have no service.log log in /var/log directory, I checked the apparmor log (the one who check mysql files permissions) and its log is empty...

dmesg | service mysql start does not show anything, just nothing, and of course mysql does not start.

---

### Post by StuartN on 2010-05-27
> **alex_time said:**
> yes but...when I run "service mysql start"

Try "service mysql**d** start", with mysqld not mysql.

> **alex_time said:**
> dmesg | service mysql start does not show anything, just nothing, and of course mysql does not start.

I can not see why you would wish to pipe the output of dmesg into service, rather than perhaps run "dmesg | tail" after a failure.

---

### Post by alex_time on 2010-05-27
> **StuartN said:**
> Try "service mysql**d** start", with mysqld not mysql.

mysqld: unrecognized service

I always user "service mysql" and not "service mysqld"

> **StuartN said:**
> I can not see why you would wish to pipe the output of dmesg into service, rather than perhaps run "dmesg | tail" after a failure.

dmesg | tail gives this, nothing about mysql


[   23.896230] Bluetooth: SCO socket layer initialized
[   24.178867] Bluetooth: RFCOMM TTY layer initialized
[   24.178898] Bluetooth: RFCOMM socket layer initialized
[   24.178900] Bluetooth: RFCOMM ver 1.11
[   27.400017] end_request: I/O error, dev fd0, sector 0
[   27.421272] end_request: I/O error, dev fd0, sector 0
[   28.480010] eth0: no IPv6 routers present
[   30.781161] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   34.101255] vmnet1: no IPv6 routers present
[   34.691254] vmnet8: no IPv6 routers present


mysqld_safe succes on running mysql server as well as mysqld, so again, what does the "service" program do? And where does it store a log?

---

### Post by alex_time on 2010-05-27
I have news

If I start mysql with mysqld and the kill it, then I am able to start it again using "service mysql start", so I really think that it is a permission issue, probably mysqld create some file that "service mysql start" cannot, but where can I look?! Is it possible that service program does no create any log file?! It is not possible to loose two dayes in something so stupid because of no log files!

---

