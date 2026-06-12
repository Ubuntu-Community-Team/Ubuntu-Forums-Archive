---
title: "MySQL PHP MyAdmin Problem"
date: 2009-07-08
forum: General Help
---

### Post by Black Mage on 2009-07-08
I'm having a problem connecting to my mysql database.I recently had to reinstall mysql database and because of a different error I couldn't fix. When I try to connect from my webserver in the same network using phpmyadmin, I get this error:

#1130 - Host 'webserver.local' is not allowed to connect to this MySQL server

And this from the command line:

bob@webserver:~$ mysql -h 192.168.1.100 -u root -p
Enter password:
ERROR 1130 (00000): Host 'webserver.local' is not allowed to connect to this MySQL server


And I have commented out the bind-address in the my.cnf. So does anyone have an idea what else can be wrong?

---

