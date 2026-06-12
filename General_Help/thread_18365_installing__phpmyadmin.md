---
title: "installing  phpmyadmin"
date: 2005-03-06
forum: General Help
---

### Post by apriest on 2005-03-06
Has anyone installed PhpMyAdmin on their warty install? I have followed the install instructuctions at: 

[http://www.phpmyadmin.net/home_page/docs.php](http://www.phpmyadmin.net/home_page/docs.php) 

I keep getting  a 'cannot load mysql extension' extension error when I try to go to

[http://localhost/myadmin/index.php](http://localhost/myadmin/index.php)

I checked phpinfo() to make sure the php was configured with mysql support but I'm stumped as to why phpmyadmin isn't finding it. I have confirmed that mysql is running  and that php is also running. I am using the lamp package that comes with Ubuntu.

Thanks for any help you can offer in advance.

---

### Post by jensyt on 2005-03-06
I installed both MySQL and phpMyAdmin just a few days ago to do some local testing. I don't know if it was necessary, but I installed php4-mysql along with MySQL and phpMyAdmin.
```
sudo apt-get install php4-mysql
```
Maybe that'll help. (Obviously, if you're using php3, use that package, etc...)

---

### Post by bpilgrim1979 on 2005-03-07
Does that install apache 1.3 or 2.0?

Obviously that won't work with PHP5.  jensyt: Did you setup PHP5 on Ubuntu with MySQL 4.1 mysqli support?

---

### Post by apriest on 2005-03-07
[QUOTE=jensyt]I installed both MySQL and phpMyAdmin just a few days ago to do some local testing. I don't know if it was necessary, but I installed php4-mysql along with MySQL and phpMyAdmin.
```
sudo apt-get install php4-mysql
```
Maybe that'll help. (Obviously, if you're using php3, use that package, etc...)[/QUOTE]
 Where is the repository please? When I run '% sudo apt-get install php4-mysql'

I get a package not found message..

---

### Post by andreabg on 2005-04-08
Hi apriest,

I've found the package in this link:

[http://packages.dotdeb.org/dists/woody/php4/](http://packages.dotdeb.org/dists/woody/php4/)


found also this one

[http://sunsite.utk.edu/ftp/pub/linux/Debian/pool/main/p/php4/](http://sunsite.utk.edu/ftp/pub/linux/Debian/pool/main/p/php4/)

hope this will help you! (I've got the same problem with phpmyadmin)


Andrea

---

