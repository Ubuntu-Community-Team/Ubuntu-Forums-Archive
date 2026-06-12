---
title: "windows, ubuntu and mysql"
date: 2010-07-16
forum: General Help
---

### Post by getmizanur on 2010-07-16
elloo all, 

i have two machines at home running ubuntu linux and windows connected by lan. on ubuntu machine i have mysql installed, how do i go about accessing ubuntu mysql database on my windows machine. 

many thanks in advance

---

### Post by RiceMonster on 2010-07-16
There's a number of ways. You could use a tool like SQLyog (which costs money). You could set up ssh, log in with PuTTy and access it from there. You could also set up phpMyAdmin

---

### Post by The Cog on 2010-07-16
MySQL clients are available for windows. Mysql-query-browser and mysql-admin are names that spring to mind.

The thing that might catch you out is that the default mysql server on ubuntu only listens on the loopback address 127.0.0.1. You need to configure this to listen on the "any" address 0.0.0.0 instead. I don't remember where this is stored - I would guess at either /etc/default/mysql or in mysql.conf (wherever that is).

Also, you must change the users permissions in mysql itself to allow logins from anywhere. Again,I can't remember the syntax, but it mught be something like username@* or username@%.

Sorry I'm so vague, but I hope it's given you ideas what to look for.

---

