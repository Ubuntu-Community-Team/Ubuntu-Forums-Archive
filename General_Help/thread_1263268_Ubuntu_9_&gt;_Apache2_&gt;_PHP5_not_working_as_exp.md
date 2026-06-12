---
title: "Ubuntu 9 &gt; Apache2 &gt; PHP5 not working as expected"
date: 2009-09-10
forum: General Help
---

### Post by nathandelane on 2009-09-10
I am trying to figure out what I need to do to get PHP working on Apache on a latest Ubuntu Desktop installation. I have installed php5, apache2 and the apache php module. When I try to load a php file in my browser from /var/www (for example [http://localhost/test.php](http://localhost/test.php)) it tries to download instead of parsing the file. When I look at /etc/apache2/httpd.conf it is empty. So what am I doing wrong?

---

### Post by X-Rated on 2009-09-10
Hi Nath or is it Elane?
Anyway I think you should read this 

[http://www.php.net/manual/en/install.unix.apache2.php](http://www.php.net/manual/en/install.unix.apache2.php)

Take note Example Install Instructions item **14** and **15**

HTH

---

### Post by mbrush on 2009-09-10
I believe the file is /etc/apache2/apache2.conf

Are you sure you installed 'apache2', 'libapache2-mod-php5' and 'php5'.

Also, did you try restarting apache?

sudo /etc/init.d/apache2 restart

Good luck

---

