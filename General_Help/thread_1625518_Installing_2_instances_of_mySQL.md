---
title: "Installing 2 instances of mySQL"
date: 2010-11-19
forum: General Help
---

### Post by cancer10 on 2010-11-19
Hi


I am running Ubuntu 10.04 at work.

I was wondering if i can install mySQL server on one of my user's account and then create another user account and install mySQL under that so will there be any conflict or any problem?



Thanks

---

### Post by DaithiF on 2010-11-19
it would be a lot simpler to use a single mysql instance but set permissions in mysql such that user A can't access database(s) belonging to user B, etc.  is this something you have considered?

---

### Post by SeijiSensei on 2010-11-19
The simplest answer is no, since mysqld starts up with root privileges then becomes the "mysql" user when it's running.  

If you want to run a second instance, create another copy of my.cnf, say my2.cnf, and assign it to a different port.  It won't start automatically; you'll need to run it manually from /etc/rc.local using the my2.cnf configuration file.  You'll need to read the MySQL manual to get the correct syntax to do so. 

If you just want to give each user a separate database, then follow DaithiF's advice above.

---

