---
title: "websever"
date: 2010-05-21
forum: General Help
---

### Post by obscurant1st on 2010-05-21
apache is the commonly used webserver in linux.
you can install it by using apt-get command.

---

### Post by WorMzy on 2010-05-21
To set up LAMP (Linux, Apache, MySQL, PHP) on ubuntu, run:
```
sudo tasksel install lamp-server
```

You can make it into a LAMPP (+Perl) by running:
```
sudo apt-get install libapache2-mod-perl2
```

---

### Post by obscurant1st on 2010-05-21
> **WorMzy said:**
> To set up LAMP (Linux, Apache, MySQL, PHP) on ubuntu, run:
```
sudo tasksel install lamp-server
```You can make it into a LAMPP (+Perl) by running:
```
sudo apt-get install libapache-mod-perl
```

LAMP is the best option for a new guy. I should have pointed out that one instead of apache2. :)
anyway thx to u. :)

---

### Post by timgood on 2010-05-21
> **WorMzy said:**
> To set up LAMP (Linux, Apache, MySQL, PHP) on ubuntu, run:
```
sudo tasksel install lamp-server
```

You can make it into a LAMPP (+Perl) by running:
```
sudo apt-get install libapache-mod-perl
```

In 10.04 (Lucid) that should be libapache2-mod-perl2

Hope this helps.

---

### Post by WorMzy on 2010-05-21
> **timgood said:**
> In 10.04 (Lucid) that should be libapache2-mod-perl2

Hope this helps.

That's what I meant, forgot the 2. :p

Thanks for spotting it.

EDIT: Missed the 2 twice, it's perl2. This is what happens when I trust my memory.

---

### Post by bodhi.zazen on 2010-05-21
LAMP is Linux Apache Mysql and PHP

If you do not need Mysql or PHP, just install apache (yes it is apache2 , these things all have versions php5 etc).

Use apt-cache

```
apt-cache search apache
```Only install the things you need (increases security).

If you need just a simple web server, look at lightthd and nginx.

Apache is, IMO, better then the above 2 with PHP, nginx is better with static content (just html without PHP or other dynamic content).

---

