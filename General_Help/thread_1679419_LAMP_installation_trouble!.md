---
title: "LAMP installation trouble!"
date: 2011-02-01
forum: General Help
---

### Post by OxentroT on 2011-02-01
The other night I was attempting to install LAMP in order to start a Wordpress Weblog and I was so tired that I fell asleep sometime after choosing a user name and a secure password. Today I tried to login to my 'phpmyadmin' and could not remember my login information =D>

I have tried completely removing all of these packages then rebooting and re installing hoping that I would be able to reset my login information but to no avail.

Any Ideas?

Thanks all!

---

### Post by clasificados on 2011-02-01
> **OxentroT said:**
> The other night I was attempting to install LAMP in order to start a Wordpress Weblog and I was so tired that I fell asleep sometime after choosing a user name and a secure password. Today I tried to login to my 'phpmyadmin' and could not remember my login information =D>

I have tried completely removing all of these packages then rebooting and re installing hoping that I would be able to reset my login information but to no avail.

Any Ideas?

Thanks all!




Check inside of /etc/phpmyadmin/config-db.php

---

### Post by OxentroT on 2011-02-01
> 
Originally Posted by: clasificados
Or Check inside of /etc/phpmyadmin/config-db.php


I have examined multiple .conf files in that directory and have found nothing in the way of a password or username within them. Is there something I should edit within these files? Could you or anyone else be a little more specific? (such a n00b!)

Thank You!

---

### Post by kukker32 on 2011-02-01
I also had same problems today i fixed it by running this

sudo /etc/init.d/mysql stop

sudo mysqld --skip-grant-tables --skip-networking & mysql -u root

UPDATE user SET Password=PASSWORD('YOUR_PASSWORD_HERE')

WHERE Host='localhost' AND User='root'

sudo /etc/init.d/mysql restart

your username is now root and the password is what you choosed above..

worked like a charm :D

---

### Post by OxentroT on 2011-02-01
Tnank You **kukker32**! I will be sure and give that a whirl!

I am still curious, however if this will effect my phpMyAdmin login as well? because I dont remember that ine either.

---

### Post by DrReaper on 2011-02-01
I had a few problems getting everything working in LAMP and wordpress. I eneded up making a clonezilla backup of the entire computer then installing. As I got each part working I made a new backup. If I messed it up I was able to go back and try over.

---

### Post by asmoore82 on 2011-02-01
> **kukker32 said:**
> I also had same problems today i fixed it by running this

sudo /etc/init.d/mysql stop

sudo mysqld --skip-grant-tables --skip-networking & mysql -u root

UPDATE user SET Password=PASSWORD('YOUR_PASSWORD_HERE')

WHERE Host='localhost' AND User='root'

sudo /etc/init.d/mysql restart

your username is now root and the password is what you choosed above..

worked like a charm :D

on Debian derived systems like Ubuntu, you can just do this:
```
sudo dpkg-reconfigure mysql-server-5.1
```

---

### Post by OxentroT on 2011-02-01
> **asmoore82 said:**
> on Debian derived systems like Ubuntu, you can just do this:
```
sudo dpkg-reconfigure mysql-server-5.1
```

Well ALRIGHT! I think that this might solve it.

THANK You asmoore82!

ROCK ON!
:guitar:

---

### Post by kukker32 on 2011-02-03
> **asmoore82 said:**
> on Debian derived systems like Ubuntu, you can just do this:
```
sudo dpkg-reconfigure mysql-server-5.1
```

well i didn't know that way..

but i will remember it :D:guitar:

---

