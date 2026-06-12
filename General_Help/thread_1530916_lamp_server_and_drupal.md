---
title: "lamp server and drupal"
date: 2010-07-14
forum: General Help
---

### Post by cordnor on 2010-07-14
Having problem with lamp server and drupal
What am I doing wrong? Can anyone pllesas help.



Installed Ubuntu 10.04 on clean HDD
 Installed LAMP via Synaptic Package Manager.
 

 tested apache with
 [http://localhost](http://localhost) and [http://localhost/index.php](http://localhost/index.php)
 it works!
 OK
 

 Created file testphp.php in /var/www with content: “<?php phpinfo(); ?>”
 tested php with
 [http://localhost/testphp.php](http://localhost/testphp.php)
 (Shows php-configuration)
 OK
 

 In Synaptic PM
 install Drupal 6.16-1
 configure DB for drupal6 with dbconfig-common
 DB = mysql
 PW = ******
 Success
 OK
 finner drupal I /usr/share/drupal6
 

 in Terminal (according to [http://drupal.org/node/43783](http://drupal.org/node/43783))
 $ a2enmod rewrite  
 Module rewrite already enabled
 OK
 

 $ /etc/init.d/apache2 restart  
 
[LIST]
[*]Restarting web server apache2
     apache2: Could not reliably determine     the server's fully qualified domain name, using 127.0.1.1 for     ServerName
[/LIST]
 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName  
 (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80  
 no listening sockets available, shutting down  
 Unable to open logs                                                                         [fail]  
 

 In browser:
 [http://localhost/drupal6/install.php](http://localhost/drupal6/install.php)
 Not Found
 The requested URL /drupal6/install.php was not found on this server.
 Apache/2.2.14 (Ubuntu) Server at localhost Port 80 



What is wrong here???????????????????

---

