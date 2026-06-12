---
title: "checking on phpinfo"
date: 2009-08-20
forum: General Help
---

### Post by krraleigh on 2009-08-20
I just installed the mysql db and php 5 on intrepid
I configured everything ... I think but
 
When I try to check to see if phpinfo is working to test my server I have a 404
 
[http://67.23.46.218/phpinfo-test.php](http://67.23.46.218/phpinfo-test.php)
 
can anyone advise?
 
Kevin

---

### Post by wojox on 2009-08-20
It's in /var/www/ ?

---

### Post by krraleigh on 2009-08-20
I am batting 1000 tonight
I found an article that states that if you have a problem viewing the output of php-test.php aka phpinfo() then you may need to add the following line to the bottom of the file:
nano /etc/apache2/apache2.conf
 
Include /etc/phpmyadmin/apache.conf
 
I did this and phpinfo() is displayed nicely
 
Thanx guys
Have a great day!
 
Kevin

---

