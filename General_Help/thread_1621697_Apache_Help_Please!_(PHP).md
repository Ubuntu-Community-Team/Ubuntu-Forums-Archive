---
title: "Apache Help Please! (PHP)"
date: 2010-11-14
forum: General Help
---

### Post by Jilles8 on 2010-11-14
Hi everyone,

I succesfully installed apache
when I go to localhost i see:

**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.


now, I made a test php script called showip.php,
but I can't accec:


var/www/
because If i paste a file there it sais
acces deneid.


but I am administrator!


thanks in advance!!
(ps new to ubuntu as you might have figured)

---

### Post by lmarmisa on 2010-11-14
You will need superuser privileges for create/modify/delete any file of the /var/www directory. This directory is owned by root.

---

### Post by Jilles8 on 2010-11-14
and how do I give myself ubersuperprivlidges?
(just installed ubuntu)

---

### Post by DeAviator on 2010-11-14
use command line
goto applications >> accessories >>terminal
change your directory
$cd /var/www

Now create your php files as superuser

$sudo gedit index.php
write you php code and save it 

gedit is a text editor
u can use the same command (gedit) to edit the file ..
Njoy!!

---

### Post by cyrus_the_virus on 2010-11-14
> **lmarmisa said:**
> You will need superuser privileges for create/modify/delete any file of the /var/www directory. This directory is owned by root.

That's right. You can do this by opening nautlius (file manager) as superuser: press ALT + F2, enter *gksudo nautilus* and then enter your password. Be careful not to remove any files elsewhere on the filesystem as that may damage the operating system!

Alternatively, a better and safer way is to create a new folder in the /var/www folder and then make your username the owner of that folder. To do this open a terminal (applications -> accessories) and enter this line by line:
```

sudo mkdir /var/www/mywebsite
sudo chown yourusername /var/www/mywebsite
sudo chmod 775 /var/www/mywebsite

```
You should then be able to put files in the /var/www/mywebsite folder as a normal user and access them via [http://localhost/mywebsite](http://localhost/mywebsite)

Good luck

---

### Post by lmarmisa on 2010-11-14
It is possible to change the place for the directory www.

I prefer to locate the www dir inside my HOME directory. I like to be the owner of these files. I consider more comfortable this solution for the development of applications.

This example shows how locate the www dir in /home/yourusername/www

Open a terminal and type:

```

mkdir ~/www
sudo gedit /etc/apache2/sites-available/default

```Then locate the two lines containing /var/www 

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot **[COLOR=Red]/var/www[/COLOR]**
    <Directory />
        Options FollowSymLinks
        AllowOverride all
    </Directory>
    <Directory [COLOR=Red]**/var/www/**[/COLOR]>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride all
        Order allow,deny
        allow from all
    </Directory>
[COLOR=Black]...[/COLOR]


```and substitute it with /home/yourusername/www

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot **[COLOR=Red]/home/yourusername/www[/COLOR]**
    <Directory />
        Options FollowSymLinks
        AllowOverride all
    </Directory>
    <Directory [COLOR=Red]**/home/yourusername/www/**[/COLOR]>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride all
        Order allow,deny
        allow from all
    </Directory>
[COLOR=Black]...[/COLOR]


```Now, save and exit.


Finally restart the service apache2:

```

sudo service apache2 restart


```Don't forget to copy the files existing in the /var/www to the new www root directory.

NOTE: some web applitactions (for example cakePHP and its tmp dir) will need to give write permission to apache2 (running as root). In such a case I use the command chmod -R a+w dir_to_write.

---

