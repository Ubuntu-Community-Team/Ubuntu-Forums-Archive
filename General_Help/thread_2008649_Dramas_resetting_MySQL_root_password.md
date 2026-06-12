---
title: "Dramas resetting MySQL root password"
date: 2012-06-23
forum: General Help
---

### Post by Phalanxer on 2012-06-23
I forgot my MySQL root password, so I stopped the MySQL service and executed:

> sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &

I then logged in as root and updated the password:

> UPDATE user SET Password = 'abc123' WHERE User = 'root';

I then quit, started the MySQL service and tried to login as root, but its not accepting the new password.

**ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)**

Does anyone know why?

---

### Post by Phalanxer on 2012-06-23
Needed:

UPDATE user SET Password = password'abc123' WHERE User = 'root'; 			 		

Solved.

---

