---
title: "Mysql root denied!"
date: 2010-02-01
forum: General Help
---

### Post by LastHylian on 2010-02-01
So, I was in the process of trying to install phpbb and in my speedy nature, I accidentally deleted the root user through phpmyadmin! Now, I can't log back in through phpmyadmin. When I try to login to mysql using

mysql -u root -p

it asks for the password. I enter it, but I always get

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

I've tried this guide 
[http://www.cyberciti.biz/tips/recover-mysql-root-password.html]("http://www.cyberciti.biz/tips/recover-mysql-root-password.html")

But still nothing! I've also completely PURGED mysql-server, the core, and the common files. Anything to do with mysql, I have purged and re-installed. Still, I got the same denied statement. I'm starting to think there is a configuration file stored somewhere else that is storing the users. Please HELP!

System OS : Ubuntu 9.10 x64

---

### Post by t4thfavor on 2010-02-01
Try mysql -u root
without -p

Otherwise that tutorial looks accurate.

---

### Post by LastHylian on 2010-02-01
> **t4thfavor said:**
> Try mysql -u root
without -p

Otherwise that tutorial looks accurate.

Tried it, but I still get

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

---

