---
title: "LAMP problems after upgrade"
date: 2006-05-10
forum: General Help
---

### Post by garner_nc on 2006-05-10
I dist-upgraded my Hoary to Breezy. Now when I try to run PHP scripts through my web server I get the following message:


Fatal error: Call to undefined function: mysql_connect() in /var/www/manage.php on line 6

It's not just this one script, it's all of them. Any ideas?

All the Best,
Doug White

---

### Post by gibson on 2006-05-10
Have you tired removing then installing apache/mysql/php

Just a hunch (i never tried lamp in hoary) but the configs may be out of date. 

you could also try dpkg --reconfigure on those packages, again, i am not sure how these are handled.

hope to help

---

### Post by garner_nc on 2006-05-10
Over the past 5 HOURS I've removed and re-installed EVERYTHING that has to do with PHP, MySQL, and Apache. I can log into my MySQL server. Running phpinfo() shows a normal functioning PHP install. A simple web page works so Apache is configured properly. I just can't get to MySQL through PHP.

   Note to self, if everythings working, DON'T MESS WITH THE SYSTEM!!

   This is REALLY annoying. 

All the Best,
Doug White

---

### Post by hardXcore on 2006-05-10
Lamp Problem?
Put New Light Bulb In!

---

### Post by FDupont on 2006-05-11
Go edit php.ini and uncomment this line "extension = mysql.so"

---

### Post by ElijahLofgren on 2006-05-11
I got tired of configuring Apache, MySQL, PHP on every distro I tried. I now use XAMPP which is Apache, MySQL, PHP and Perl all bundled together and set up to work out of the box.
Check it out: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by garner_nc on 2006-05-11
I finally removed apache and PHP. Downloaded and installed both from source. All is well now.

   Seems a lot of people have had this issue but there seems to be no easy fix for it. I searched countless web pages looking for information on this.

   Compiling PHP from source requires "Flex" (it's inthe repositories) and that the "--with-mysql" switch be set. Overall it's been a good learing experience though it wasn't a good time to have this happen.

All the Best,
Doug White

---

