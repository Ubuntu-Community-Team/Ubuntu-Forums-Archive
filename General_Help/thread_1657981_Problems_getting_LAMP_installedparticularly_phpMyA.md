---
title: "Problems getting LAMP installed/particularly phpMyAdmin"
date: 2011-01-01
forum: General Help
---

### Post by shad0wslay3r on 2011-01-01
I switched to Linux recently to start learning PHP and MySQL, and used this video on youtube to learn how to install all the desired packages and stuff

[http://www.youtube.com/watch?v=0Fvn8WOfxKY](http://www.youtube.com/watch?v=0Fvn8WOfxKY)

Everything got installed correctly up until 6:48, at the time I didn't know that you need to press space bar to get the star in the box to select the desired configuration, thusly causing myPhpAdmin not to be installed correctly and localhost/myphpadmin not showing up.  

So after trying to reinstall it, and then removing all the packages and re installing, this specific set up for the db-config will not show up.  Is there a way to completely remove all of these packages and start fresh?

I also tried installing the LAMP server thing, but also myphpadmin fails to get installed properly.  

Any help is appreciated greatly, if more information is needed I will try to post back asap

---

### Post by fragos on 2011-01-02
Run Synaptic Package Manager, click Edit, then "Mark Packages by Task...", select the LAMP server, and click Apply icon. Apache, MySQL and PHP will install.

The LAMP install requires a bit of configuration to run PHP code. The file to be edited is /etc/apache2/httpd.conf. If it's already there it's probably empty, if not create it. Place the following three lines in it. The

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

The web server will have to restart for the configuration changes to take effect. The next time your sytem boots will do that or run the following CLI. This always works for me.

sudo /etc/init.d/apache2 restart

---

