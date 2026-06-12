---
title: "I installed PHPMyAdmin and MySQL, How do I access them?"
date: 2009-07-26
forum: General Help
---

### Post by sois on 2009-07-26
I have the apache server set up, it appears to be working.   I dont know where my public_html folder is though.  

Also, how do I access PHPMyAdmin?  Thanks!

---

### Post by DaithiF on 2009-07-26
/var/www
and
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

cheers

---

### Post by sois on 2009-07-26
> **DaithiF said:**
> /var/www
and
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

cheers

I don't seem to have permission to that folder.  Will I always have to log on with sudo to work in this folder?

Secondly,  [http://localhost/phpmyadmin](http://localhost/phpmyadmin) doesn't work.  I get 404 not found.

---

### Post by DaithiF on 2009-07-26
by default you won't have full access to /var/www, but typically you would use sudo to change ownership of the /var/www directory to the www-data user that your apache webserver runs as.  You could also permission your own user id with access by adding yourself to the www-data group.  Really there are many ways of approaching this so you should probably do some research on user and group permissions and then decide on an approach which makes sense for you.  

One way would be:
sudo chown -R www-data.www-data /var/www
sudo usermod yourname -G www-data

Secondly, Phpmyadmin installs itself by default with a url of /phpmyadmin -- I assumed you were running apache/phpmyadmin on your local machine, hence the [http://localhost](http://localhost) part.
So, first question:
is it your local machine that you have installed apache on, or another machine?  If another machine, then use its IP address instead of localhost
secondly, if it is indeed your local machine, can you load [http://localhost/](http://localhost/) itself -- you should see a default It works! message if apache was installed correctly.
If this step is ok, then check /etc/apache2/conf.d/phpmyadmin.conf  -- at the top will be a line saying something like Alias /phpmyadmin /usr/share/phpmyadmin.  The piece after Alias is the url you need to go to

good luck

---

### Post by sois on 2009-07-26
> **DaithiF said:**
> 
Secondly, Phpmyadmin installs itself by default with a url of /phpmyadmin -- I assumed you were running apache/phpmyadmin on your local machine, hence the [http://localhost](http://localhost) part.
So, first question:
is it your local machine that you have installed apache on, or another machine?  If another machine, then use its IP address instead of localhost
secondly, if it is indeed your local machine, can you load [http://localhost/](http://localhost/) itself -- you should see a default It works! message if apache was installed correctly.
If this step is ok, then check /etc/apache2/conf.d/phpmyadmin.conf  -- at the top will be a line saying something like Alias /phpmyadmin /usr/share/phpmyadmin.  The piece after Alias is the url you need to go to good luck

1.  Local install.
2.  When I enter [http://localhost/](http://localhost/), I do not get a "this works" message.  Instead I get this:

**Index of /**

 [IMG]http://localhost/icons/blank.gif[/IMG][Name]("http://localhost/?C=N;O=D")[Last modified]("http://localhost/?C=M;O=A")[Size]("http://localhost/?C=S;O=A")[Description]("http://localhost/?C=D;O=A") 

Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80

3.  I do not see phpmyadmin.conf in the conf.d directory of apache2.

---

### Post by DaithiF on 2009-07-27
I'm sorry but I don't think your installation has worked.  What steps did you follow to install apache, php, mysql ?

You might want to try following a guide like this:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

hope this helps

---

### Post by credobyte on 2009-07-27
For phpMyAdmin:
```
sudo gedit /etc/apache2/apache2.conf
```
Add:
```
Include /etc/phpmyadmin/apache.conf
```


For testing your webserver:
```
sudo gedit /var/www/index.php
```
Add:
```
<?php phpinfo(); ?>
```

Restart Apache:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by sois on 2009-07-27
YES!  I'm up and at them!  Thank you for all of your help!

---

