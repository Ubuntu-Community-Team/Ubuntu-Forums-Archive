---
title: "mysql error"
date: 2009-07-04
forum: General Help
---

### Post by babbar.ankit on 2009-07-04
babbar@babbar-laptop:~$ mysql -v -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'babbar'@'localhost' (using password: YES)

Plz help, i have even tried it using sudo

---

### Post by LoneWolfJack on 2009-07-04
```
mysql -uroot -p<yourpass>
```

---

### Post by babbar.ankit on 2009-07-04
It didn't worked

---

### Post by LoneWolfJack on 2009-07-04
can you be less specific please?

---

### Post by babbar.ankit on 2009-07-04
babbar@babbar-laptop:~$ mysql -v -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'babbar'@'localhost' (using password: YES)

Any of the commands for mysql are not working 
What should i do?
I have changed the blind= localhost
Do i need to change any other setting in \etc\mysql\my.cnf

---

### Post by Celauran on 2009-07-04
Have you set up any users other than root? If not, you'll need to do that first.

```
mysql -u root -p
```

You will be prompted for the MySQL root password. From there you'll need to create a separate user.

---

### Post by babbar.ankit on 2009-07-04
babbar@babbar-laptop:~$ mysql -u root -p 
Enter password:
 ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES) 

(#6 try)

---

### Post by Celauran on 2009-07-04
I'd take a look how to [reest root password](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html), then.

---

### Post by Umeme on 2009-07-06
I'm a Newbie here. Tried installing sound and video players from the application menu using 'all open source application' but the laptop ran out off power during 'configuring mysql' and went off. Now it won't load the Gnome window. Please help. Using 9.04.

---

