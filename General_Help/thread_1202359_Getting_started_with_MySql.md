---
title: "Getting started with MySql"
date: 2009-07-02
forum: General Help
---

### Post by Bob Unitt on 2009-07-02
Gentlefolk,

I'm trying to get MySql installed locally on my machine, with a view to developing database programs in Java. I'm on ubuntu 9.04 'Jaunty'.

My background is mainly Windows/C/Sybase SQLAnywhere DB, so I probably have a mindset problem and I'm failing to see the obvious...
 
I've installed the following packages via Synaptic :-

libdbd-mysql-perl
libmysqlclient15off
libmysqlclient16
libmysql-java
libqt4-sql-mysql
mysql-admin
mysql-client-5.0
mysql-common
mysql-doc-5.0
mysql-gui-tools-common
mysql-navigator
mysql-query-browser
mysql-server-5.0
mysql-server-core-5.0

Having searched the forums, it would appear that I next need to set the MySql password. I've tried various commands suggested on the forums, but whatever I try to do ends up with an error message of the form "ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)".

I've obviously missed something somewhere along the way - any suggestions, please ?

TIA

---

### Post by mthalis on 2009-07-02
Normally they ask passwd in installation process. Is it happen or not?

---

### Post by Bob Unitt on 2009-07-02
> **mthalis said:**
> Normally they ask passwd in installation process. Is it happen or not?

No - I installed via Synaptic, and it asked me no questions at all. 

Is there some kind of configuration program I should be running ?

---

### Post by alphacrucis2 on 2009-07-02
> **Bob Unitt said:**
> No - I installed via Synaptic, and it asked me no questions at all. 

Is there some kind of configuration program I should be running ?

When you install mysql-server via synaptic it should ask for the Mysql admin password to be set at the end of the installation. Did for me anyway. You can't miss it. It displays a humongous dialog box asking you to enter a root password for Mysql then it asks you to enter it again to confirm.


Edit: Just a thought. Maybe that only happens if you install the mysql-server meta package?

---

### Post by mthalis on 2009-07-02
I installed it, but no passwd ask?

---

### Post by snek on 2009-07-02
```
sudo dpkg-reconfigure mysql-server
```
This might do the trick.. Otherwise you can always change it command-line, have a look [HERE]("http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/")

---

### Post by Bob Unitt on 2009-07-02
Found the cause of my problem - installing via Synaptic gives MySql the system administration password by default, which is why it never prompted me for a new one on installation - I'm now working OK.

Thanks.

---

