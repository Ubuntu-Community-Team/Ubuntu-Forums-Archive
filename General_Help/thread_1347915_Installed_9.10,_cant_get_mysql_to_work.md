---
title: "Installed 9.10, cant get mysql to work"
date: 2009-12-06
forum: General Help
---

### Post by WeaponsTheyFear on 2009-12-06
Hey guys, having a bit of a problem.  I just installed 9.10 the other night fresh and have ran through apt-get to get apache2, php 5, mysql and phpmyadmin.  

When I start my php app, I am told that mysql_connect function does not exist, although I can go into terminal and use /etc/init.d/mysql start.

I remember last time I installed I was able to do so through one single command, and i believe one single package, but this time I used a series of apt-get's.

Anyone experiencing this or know how to solve?

---

### Post by irishbreakfast on 2009-12-10
Did you figure this out? It is nice to know it is not just me. I am new to php/mysql and doing a lot of getting nowhere.

I just installed php5-mysql and that hasn't helped either.

---

### Post by irishbreakfast on 2009-12-10
Took a closer look at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
and saw that I needed libapache2-mod-auth-mysql.

Now to figure out how to access the existing database. "Access denied"

---

