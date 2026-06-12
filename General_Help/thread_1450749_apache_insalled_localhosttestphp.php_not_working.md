---
title: "apache insalled //localhost/testphp.php not working"
date: 2010-04-09
forum: General Help
---

### Post by Rockling on 2010-04-09
Installed apache typed in [http://localhost/](http://localhost/) got the It Works page back. Then installed php and checking to see if all is ok  wrote a testphp.php file with <?php phpinfo(); ?> 
opened up firefox typed in [http://localhost/testphp.php](http://localhost/testphp.php) and firefox brings up a window asking what to do with this php file.
How do i get it to accept php files.

Cheers
Des

---

### Post by webtechquery on 2010-04-09
Hi,

Well, I suggest you to check out the following URL for installing LAMP, and see if you have missed out something:

[http://www.webtechquery.com/index.php/2010/01/install-php-mysql-and-apache-lamp-on-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/01/install-php-mysql-and-apache-lamp-on-ubuntu-linux/)

---

### Post by Rockling on 2010-04-09
Thanks Solved it 
Forgot to restart apache server

sudo /etc/init.d/apache2 restart

---

