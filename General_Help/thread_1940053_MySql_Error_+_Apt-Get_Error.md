---
title: "MySql Error + Apt-Get Error"
date: 2012-03-12
forum: General Help
---

### Post by Dr Widdleguy on 2012-03-12
Well,

Today for some odd reason my server crashed. For some reason Apache was killed. When I tried restarting Apache it gave multiple errors of directories not being found so I created a couple of new directories (mainly a place for Apache to send error logs) and it finally restarted. After that I noticed that MySql was down. Every time I try to connect to MySql through the terminal I get > "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)". I've looked everywhere before creating the new mysqld.sock file and even used the find commands and etc. to no avail. I looked at the directory where my databases are suppose to be stored and that directory structure is gone. When I tried removing then re-installing MySql I get the error of > "E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)". I've tried doing the dpkg --configure -a and the dpkg -i commands but they've done nothing for me. Before I had to create new status directories and a new dpkg directory to even of gotten to this point. I'm clueless as to what exactly happened, and clueless as how to further repair whatever has been screwed up. I was trying to avoid a fresh install, but if all my databases are completely gone then I have nothing to lose. :/ I'm not entirely linux literate, so go easy on me please. Any help is greatly appreciated. Thanks. 

- Dr Widdleguy

---

### Post by garyed on 2012-03-12
Have you checked /var/lib/mysql directory to see if your databases are still there? 
If so then you could back up the mysql directory before you do any experimenting.

---

### Post by Dr Widdleguy on 2012-03-12
I had to create an apt directory and dkpg directory earlier in /var/lib/ because everything in it vanished. :/ 

Guessing that's the only location my databases would of been?

---

### Post by mikemcginn on 2012-03-13
I am having problems too. This has been running on my laptop well for ages. The update this morning failed. I did "dpkg --configure -a", but that did not fix anything currently trying a reinstall of the server, but it has been hung on the "Setting up mysql-server-5.1 (5.1.61-0ubuntu0.10.04.1) ..." step for 17 minutes now, so I think my problems are just beginning.

---

