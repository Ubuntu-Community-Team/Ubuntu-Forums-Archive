---
title: "Ubuntu Server (Gnome GUI) MySQL problem"
date: 2010-08-25
forum: General Help
---

### Post by LuniTux on 2010-08-25
Hello,

I have an Ubuntu 9.10 Server with the Gnome GUI install via instructions at:

[http://ubuntuforums.org/showthread.php?t=1155961]("http://ubuntuforums.org/showthread.php?t=1155961")

Everything seems to be setup ok except for the MySQL. I can connect the MySQL on the local machine but not through other machines via ODBC. I checked the ports and they are open. I can ssh to the machine as well. The MySQL is also on the original 3306 port. This is the error that I am getting.

Test Results:

Connection Failed: [HY000][MySQL][ODBC 5.1 Driver]Can't connect to MySQL server on 'xxx.xxx.xxx.xxx' (10061)

I have been looking for a couple days now and still can not find the solution. Any ideas?

Thanks in advance

---

### Post by uszatan on 2010-08-25
Hi,

Have you commented out this line in a /etc/mysql/my.cnf config file?:


# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
**# bind-address            = 127.0.0.1**

---

### Post by LuniTux on 2010-08-25
Yay!

I figured it was something simple

Thanks

---

