---
title: "How do I set up php on my new Linux system?"
date: 2011-11-07
forum: General Help
---

### Post by glennbates on 2011-11-07
Looking to set up php but may not need MySQL installed.

---

### Post by nickleboyblue on 2011-11-07
Well, that depends on the Linux system.  If it's Ubuntu, it's not too bad.  Here's what you will need:

Apache2 - server
PHP5 - the language pack
MySQL OR PostgreSQL (OR some incredibly non-standard database) - RDBMS
Popcorn - progress bars are boring.

A really good guide can be found here: [Installing LAMP on Ubuntu]("http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/")

Installing all of the needed packages is possible and even rewarding, but to avoid hours on end of banging your head against the wall, the above guide simplifies things down to a minimum.

You will probably want to modify permissions on your document root as well to make it possible to edit documents and create folders without being root.  There are two approaches to this:  Change your document root to /home/*username*/www/ , or add your user to the www-data group, change ownership recursively on the /var/www/ file to www-data, and chmod the /var/www/ file recursively to allow the editing, removing, adding, and execution of files by the file owner, i.e. www-data.  

In addition to PHP, you'll probably want a graphical database gui.  If you plan on using MySQL, you can install phpmyadmin from synaptic and navigate your internet browser to it once it's installed.  If you use PostgreSQL, I suggest you use phppgadmin, which is similar to the first one I mentioned.  These tools can be either invaluable or worthless, depending on your development style.

Hope that helps.

---

### Post by utnubuuser on 2011-11-07
Lullabot has a good video tutorial for installing a Drupal test environment, (localhost), in Ubuntu....

If you followed their tutorial, minus the installation of Drupal, which comes at the end of the tutorial, your PHP environment would be pretty well set...

Lullabot: [http://www.lullabot.com/videos/install-local-web-server-ubuntu]("http://www.lullabot.com/videos/install-local-web-server-ubuntu")

---

### Post by fragos on 2011-11-08
After installing Apache and PHP you'll still need to configure Apache for PHP. Make sure there is an /etc/apache2/httpd.conf that has the following three lines which allow execution of PHP:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

### Post by linuxwin2 on 2011-11-09
You can configure your apache and write a test php page
under /var/www/ write test.php
[code]
<?
phpinfo();
?>
Restart apache
$ sudo /etc/init.d/apache2 start
Test with browser
$firefox http://127.0.0.1/test.php

---

### Post by PsyclonJohn on 2011-11-09
sudo apt-get install tasksel (you may already have it)
sudo tasksel 

select LAMP Sever (space bar) then hit enter

go through the installation

sudo apt-get install phpmyadmin

open terminal and type in: gksudo nautilus

go to the path of /usr/share/phpmyadmin and copy it into your /var/www folder

---

