---
title: "Help, bug in PHPMyAdmin killing me!"
date: 2010-09-24
forum: General Help
---

### Post by micha8l on 2010-09-24
I installed PHPMyAdmin on Ubuntu 10.04:

```

sudo apt-get install libapache2-mod-auth-mysql phpmyadmin
[Entered database password]
[Entered application password]

```

During the prompts during the instillation I made a mistake, with me being a big newbie, I never hit enter to select the HTTP server for PHPMyAdmin to use.

So, I restarted Apache, tried [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and... it didn't work. I try to uninstall PHPMyAdmin with:

```

sudo apt-get purge libapache2-mod-auth-mysql phpmyadmin

```

And I get this message:
> 
An error occurred while removing the database:                            &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; mysqldump: Got error: 1049: Unknown database 'phpmyadmin' when selecting  &#9618; 
 &#9474; the database                                                              &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; For some reason it was not possible to perform some of the actions        &#9618; 
 &#9474; necessary to remove the database for phpmyadmin.  At this point you have  &#9618; 
 &#9474; two options: you can find out what has caused this error and fix it, or   &#9618; 
 &#9474; you can refuse the offer for help removing the database (the latter       &#9618; 
 &#9474; implies you will have to remove the database manually).                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; If at this point you choose "retry", you will be prompted with all the    &#9618; 
 &#9474; configuration questions once more and another attempt will be made at     &#9618; 
 &#9474; performing the operation. "retry (skip questions)" will immediately
    attempt the operation again, skipping all questions.  If you choose       &#9618; 
 &#9474; "abort", the operation will fail and you will need to downgrade,          &#9618; 
 &#9474; reinstall, reconfigure this package, or otherwise manually intervene to   &#9646; 
 &#9474; continue using it.


Help?

---

### Post by micha8l on 2010-09-24
bump

---

### Post by micha8l on 2010-09-24
Silly me, I forgot to put the question: I want to completly remove phpmyadmin, but the error ^ is stopping me

---

### Post by micha8l on 2010-09-24
bump

---

### Post by micha8l on 2010-09-25
regretful bump

---

### Post by 666f6f on 2010-09-25
Hmm, you could try creating a dummy phpmyadmin database.

---

### Post by junapp on 2010-09-25
looks like an 'easy' way would be to create a phpmyadmin database in your mysql server.

---

### Post by micha8l on 2010-09-26
Thanks guys, that's genius - worked perfectly

From BASH I ran:

```

sudo su
mysql -p
create database phpmyadmin
sudo apt-get purge libapache2-mod-auth-mysql phpmyadmin 

```

I thought there would be more to it than that, obviously not.
Guess I've learned to exhaust the easy possibilities before the advanced.

---

### Post by junapp on 2010-09-27
good to see you got it.

might be worth pointing out that this would also work and argueably might be preferred over "sudo su".
```

mysqladmin -u root -p create phpmyadmin

```
provided you've set a root password in the mysql database.
see:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Alternatively](https://help.ubuntu.com/community/ApacheMySQLPHP#Alternatively)

---

### Post by captinkid on 2010-11-15
I had the same error upgrading a 10.04 server to 10.10, your solution worked wonders, pure awesome!

Thanks!

:P

> **junapp said:**
> good to see you got it.

might be worth pointing out that this would also work and argueably might be preferred over "sudo su".
```

mysqladmin -u root -p create phpmyadmin

```
provided you've set a root password in the mysql database.
see:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Alternatively](https://help.ubuntu.com/community/ApacheMySQLPHP#Alternatively)

---

### Post by Dawa Lhamo on 2012-11-24
> **junapp said:**
> good to see you got it.

might be worth pointing out that this would also work and argueably might be preferred over "sudo su".
```

mysqladmin -u root -p create phpmyadmin

```
provided you've set a root password in the mysql database.
see:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Alternatively](https://help.ubuntu.com/community/ApacheMySQLPHP#Alternatively)

Oh, thank you!  I hit this error while upgrading to 12.04, and this fixed it so I could continue my upgrade.  You rock! :KS

---

### Post by wildmanne39 on 2012-11-24
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

