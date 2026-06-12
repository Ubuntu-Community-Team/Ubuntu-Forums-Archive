---
title: "MYSQL: ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password:"
date: 2009-08-26
forum: General Help
---

### Post by justinp on 2009-08-26
Hi, i get the above error when trying to log into mysql using mysql -u root -p. I have uninstalled and reinstalled mysql and get the same error. I definately have the correct password and all threads i have found suggest that the password be reset. When i reset the password i get the same error no matter what. Any ideas would be appreciated.

Justin

---

### Post by dmonkey on 2009-08-26
If you are sure that the password is correct (I would also say that it seems to be the problem), perhaps you have deleted the root user? Or perhaps 'localhost' is not an assigned host for root. Try

mysql -u root -h 127.0.0.1 -p

or 

mysql -u root -h <my_host_name> -p

and see if this works. Although if you say that you have reinstalled from scratch, I don't really see how this is possible. How did you reinstall? Were you sure to purge all configuration files?

---

### Post by MartinEve on 2009-08-26
Follow the instructions on this wiki page: [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

It will tell you to start the table with a temporary skip-grants option and then how to reset the password.

---

