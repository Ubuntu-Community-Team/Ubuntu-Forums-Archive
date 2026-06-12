---
title: "using mysql"
date: 2006-05-04
forum: General Help
---

### Post by jeisma on 2006-05-04
hello!

on my ubuntu 5.10 system, after installing mysql-server. i did this:

mysqladmin -u root password mypassword

when i do :

mysql -u root -p

i get this:

ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)

what's missing?

thanks!

---

### Post by byenary on 2006-05-04
Do this and your ready to rock and roll

[http://dev.mysql.com/doc/refman/5.0/en/adding-users.html](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)

actualy just this part will do

shell> mysql --user=root mysql


After connecting to the server as root, you can add new accounts. The following statements use GRANT to set up four new accounts:

mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'localhost'
    ->     IDENTIFIED BY 'some_pass' WITH GRANT OPTION;

---

### Post by cwhamsun on 2006-05-04
Might have to do with having to run it as root? try putting "sudo" in front of it? there are variations of sudo for gnome or kde, "gksudo"? I think, I am not quite sure what they are specifically for though, besided having something to do with the program being specific to the window manager you are using. So i would try using "sudo" in front of it, it may require some flags also, but I am not sure how those work either I am used to operating in strict root mode, just started using ubuntu haven't quite got the hang of all the root vs. sudo differences.

---

