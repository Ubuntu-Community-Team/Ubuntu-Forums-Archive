---
title: "MySQL Issue"
date: 2012-04-29
forum: General Help
---

### Post by SwaroopKunduru on 2012-04-29
On my Ubuntu 12.04.

Database connection donot work. I installed MySQL with software manager Installed MySQL Client/Server.

I could able to work on MySQL directly. When I am trying to connect from java program it is not connecting. The error I am getting is no response from database.

I then unInstalled by remove button and installed MySQL client/Server by command line. I have the same issue.

In both cases I am trying to connect from java program it is not connecting. The error I am getting is no response from database but I can work on MySQL database directly. 

I tried with SquirrelSQL client it don't work.

Please help me resolve this issue.

Thanks in advance.

---

### Post by SeijiSensei on 2012-04-29
By default MySQL listens only on the localhost (127.0.0.1) interface.  Are you trying to connect to a different interface?  If so, you need to edit my.cnf and restart MySQL.

Also MySQL uses 'user'@'host' usernames for authentication which limit 'user' to connections from 'host'.  Did you create a specific username for your application that includes the proper host part?

---

### Post by SwaroopKunduru on 2012-04-29
Issu resolved.

When upgrading fro some reason the older version still exists. I used following command on terminal 

sudo apt-get --purge remove mysql-server mysql-common mysql-client

and re-installed MySQL server through software manager.

I can able to connect to database.

Regards,

Swaroop Kunduru.

---

