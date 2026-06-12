---
title: "mysql not starting? ubuntu 10.10"
date: 2011-04-09
forum: General Help
---

### Post by Adrienk on 2011-04-09
i installed mysql 5.1, the workbench and glassfish along with netbeans for an application I plan to build using the java EE.

Glassfish is on local host 8080 and when I installed mysql after that, trying to start mysql from command prompt or even connecting through the workbench gives me error. for example going through the terminal and just typing mysql gives me:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

what should I do so both servers can run at the same time when deploying my application?
on windows this is all handled for me. but apparently thats not the case on ubuntu

---

### Post by Adrienk on 2011-04-09
I need help please respond

---

### Post by SeijiSensei on 2011-04-09
Did you install **mysql-server** as well as the client?

---

