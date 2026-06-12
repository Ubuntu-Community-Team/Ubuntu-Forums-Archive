---
title: "php problem"
date: 2006-05-30
forum: General Help
---

### Post by wizzkid on 2006-05-30
I installed php5 and apache2, 

PHP
php5, php5-cgi, php5-cli, php5-common, php5-mysql, php5-mysqli, php-pear
APACHE
apache2, apache-common apache2-mpm-prefork, apache2-utils, lilapache2-mod-php5

Then,  documentindex and add index.php.. however, when i browse php files I encounter this issue. see this snapshot [http://www.leeph.net/logs/nophp.png]("http://www.leeph.net/logs/nophp.png")

Also, I enounter this error "*apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName*" when I start apache2. i know where i can configure this on the old apache, its just in the httpd.conf, but in apache2, i was confused. :-(

Hope you could help.. thanks.

---

### Post by wizzkid on 2006-05-31
any help from here  ? :)

---

### Post by nodgesoft on 2006-05-31
apache2 has its config file in a subdir i believe /etc/apache2/.....

it should end in .conf i think its httpd.conf or something simliar. Just look around for /etc/apache dir

-Matt

---

### Post by disturbed1 on 2006-05-31
Firefox bug :confused: 

I've seen a few errors on PHP pages. Try using Opera or another browser that doesn't use Gecko.

---

### Post by nodgesoft on 2006-05-31
Nah it just means that apache isnt detecting the php install - sounds like a httpd.conf error.

Dont forget to look in sites-enabled and site-available.

-Matt

---

### Post by radiobrain on 2006-06-21
Hello,
I have got the same problem and i found in /etc/hosts
127.0.0.1       localhost
127.0.1.1       jungle

May this cause the probleme of installation? And why 'jungle' isn't in the localhost line. My server is named 'jungle'. It should be in the localhost line like
127.0.0.1    localhost   jungle
isn't it ?

If you find an issue, can i also know ?

thx

---

### Post by Randomskk on 2006-06-21
Make sure PHP is in the /etc/apache2/modsenabled folder, if not run this command:
sudo a2enmod
and choose the PHP you want loaded from the list (probably you want the apahce module "php5")

---

