---
title: "PHP files not parsing in Ubuntu"
date: 2012-02-28
forum: General Help
---

### Post by DeathShot on 2012-02-28
I've had this problem on Windows so I came back to Ubuntu in hopes that a fresh system will install PHP right. I installed Apache2 and PHP from the command line, you know the whole Sudo Apt-get install business and was silly enough to think that it would work out of the box. Naturally, as things are with the world... it did not.

So I have googled my problems and tried most of the things they had suggested, to no avail. It could just be that I am doing things wrong, I am a windows user and a bit rusty on my commend line.

Apache works so long as I don't try and display a PHP file.

I am running 11.10 Desktop edition, NOT server edition because this isn't for a sever this is for recreational coding and web design.

---

### Post by lisati on 2012-02-28
What exactly is happening? Is the PHP being displayed as PHP code in your browser? Is your browser trying to download a file?

---

### Post by DeathShot on 2012-02-28
> **lisati said:**
> What exactly is happening? Is the PHP being displayed as PHP code in your browser? Is your browser trying to download a file?

I should have mentioned this, duh. Forgive me it's late. In Ubuntu it asks you to download the file, in Windows it shows me the code.

---

### Post by lisati on 2012-02-28
Have a look here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5)

---

### Post by athampan on 2012-02-28
Could you list all the apt-get install commands that you used?  Did you also do this:

```
sudo apt-get install libapache2-mod-php5
```

---

### Post by DeathShot on 2012-02-28
> **athampan said:**
> Could you list all the apt-get install commands that you used?  Did you also do this:

```
sudo apt-get install libapache2-mod-php5
```

```

sudo apt-get install apache2 
sudo apt-get install php5 
sudo apt-get install libapache2-mod-php5 
sudo /etc/init.d/apache2 restart

```

> Have a look here: [https://help.ubuntu.com/community/Ap...shooting_PHP_5]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5")
I will go over your link and see if it helps, though I think I might have already stumbled upon it at some point.

---

### Post by DeathShot on 2012-02-28
I went to that link [FONT=monospace]and ran "[/FONT]sudo a2enmod php5" and the results are interesting?

```
ERROR: Module php5 not properly enabled: /etc/apache2/mods-enabled/php5.load is a real file, not touching it

```

I'm not sure what that means, php5.load is supposed to be in mods enabled, isn't it?

---

### Post by DeathShot on 2012-02-28
I completely purged everything, PHP5, Apache2, and anything even remotely related to it and installed it from scratch again. I am still getting the exact same errors. Any ideas?

---

### Post by dragonfly41 on 2012-02-28
clear browser cache

do you have short tags on or off in php.ini ?

try terminal command [COLOR=DarkGreen]**locate php.ini**[/COLOR] to find location of php.ini

try a simple test.php
```
<?php phpinfo(); ?>
```

---

### Post by DeathShot on 2012-02-28
Well I located the multiple locations of index.php
/etc/php5/apache2/php.ini
/etc/php5/apache2filter/php.ini
/etc/php5/cli/php.ini
/usr/share/doc/php5-common/examples/php.ini-development
/usr/share/php5/php.ini-production
/usr/share/php5/php.ini-production-dist
/usr/share/php5/php.ini-production.cl[FONT=Verdana]

[/FONT] 

It should just be the default, which if I know my php (which I better) php 5 uses <?php ?> at least that is how I have always done it. Though it doesn't matter because it asks me to download the file anyways  simply because of the php extension. The test file doesn't work because it asks me to download it.

---

### Post by azmyth on 2012-02-28
Go to your /etc/apache2/mods-enabled and display the files with ls. Look for a php5.load file and a php5.conf file. Do you have these files and what are their contents.

---

### Post by dragonfly41 on 2012-02-28
have you run this ..

**[COLOR=Navy]sudo apt-get install libapache2-mod-php5 php5-cli php5-common php5-cgi[/COLOR]**

---

### Post by DeathShot on 2012-02-28
> **azmyth said:**
> Go to your /etc/apache2/mods-enabled and display the files with ls. Look for a php5.load file and a php5.conf file. Do you have these files and what are their contents.

Well here is the ls:
```
michael@ubuntu:/etc/apache2/mods-enabled$ ls
alias.conf          autoindex.load  mime.load        setenvif.load
alias.load          cgi.load          negotiation.conf    ssl.conf
auth_basic.load       deflate.conf    negotiation.load    ssl.load
authn_file.load       deflate.load    php5.conf        status.conf
authz_default.load    dir.conf          php5.load        status.load
authz_groupfile.load  dir.load          reqtimeout.conf    suexec.load
authz_host.load       env.load          reqtimeout.load
authz_user.load       include.load    rewrite.load
autoindex.conf          mime.conf       setenvif.conf
```

The content of php5.conf are as follow:
```
<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
    SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
    SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>
```

The contents of php5.load are:
```

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

Also I should note that all of these files are read only. I can not edit, move, or even delete anything of them without sudo or nautilus.

---

### Post by dragonfly41 on 2012-02-28
And in 
/etc/apache2/sites-available/default

does this point to /var/www/

or 

/home/*/public_html/

may need to be changed here ..

---

### Post by DeathShot on 2012-02-28
> **dragonfly41 said:**
> have you run this ..

**[COLOR=Navy]sudo apt-get install libapache2-mod-php5 php5-cli php5-common php5-cgi[/COLOR]**

I am not sure, it looks like something that was suggested on one of the tech blogs I was reading to solve the problem before I came here, but as far as I know it never worked then. I did it just now though and it certainly did something, though it didn't fix the problem, but it least it didn't throw any errors.

> And in 
/etc/apache2/sites-available/default

does this point to /var/www/
It does in fact point to /var/www though when I used to run apache on windows, when ever I went to localhost in my browser it would show me the index.php page, here it doesn't (nor does it offer to let me download it)

---

### Post by dragonfly41 on 2012-02-28
If your web content (e.g. test.php) is in /home/yourusername/public_html

and not in default location .. /var/www

you will need to edit the default file .. which is read only

to edit .. run

gksudo gedit /etc/apache2/sites-available/default

and then edit the first few lines to amend .. thus (I assume username is michael).

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

#    DocumentRoot /var/www
    [COLOR=DarkRed]DocumentRoot /home/michael/public_html[/COLOR]

    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
#    <Directory /var/www/>
        [COLOR=DarkRed]<Directory /home/michael/public_html/ >[/COLOR]

.... etc. unchanged


then restart apache and reload files using Cntrl + F5 to clear cached file.

[COLOR=DarkRed][EDIT]

Added this link ..

[http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#specifyDocumentRoot](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#specifyDocumentRoot)
[/COLOR]

---

### Post by DeathShot on 2012-02-28
Erm sorry you lost me....  public_html?
My files are all in the /www folder... it's just the localhost isn't going anywhere which means either something is wrong with apache or I am doing something wrong. I don't have a public_html directory either, should I have?

---

### Post by azmyth on 2012-02-28
Where is the php script? In which folder /var/www ?

so if you add a test.php script into the /var/www folder you should point your browser to 

[http://localhost/test.php](http://localhost/test.php)

assuming you're on the local PC.

---

### Post by DeathShot on 2012-02-28
I did what dragonfly said to do, I don't know if that solved the problem or not but when I went to localhost/test.php it did work... however when I right click test.php and open it with firefox it still asks me to download the file. So I guess apache does pars my php files, but if php works why can't I just open them? It seems nonsensical that I will have to actually navigate to a page each and every time I want to check out a minor edit.

Figuring out the last part of that would be very much appreciated, but at least I can start working... as strange as this current set up may be, so I appreciate all the help you guys gave me.

---

### Post by dragonfly41 on 2012-02-29
Just a note to explain the logic of the last post  ..

The content of your php5.conf contains this ..

<IfModule mod_userdir.c>
<Directory[COLOR=Red] /home/*/public_html[/COLOR]>
 php_admin_value engine Off
</Directory>
</IfModule>


and that is why I thought you had your web content in your /home folder rather than your /root folder .. the default in /root is in fact /var/www

In my own setup I have ubuntu installed across two partitions ..  /root and /home partitions .. so my apache/php5 web content is not deleted when I have to reinstall ubuntu.

The link I posted above explains DocumentRoot.

If you prefer to keep your content in /var/www then you can reverse the change.

The issue you have is right clicking on your file in firefox to edit it.

Try installing Geany and then right click on your php files and open in Geany editor to edit the php file.

[COLOR=DarkSlateBlue]**sudo apt-get install geany**[/COLOR]

There are many other php editors you can try.   
You could setup a localhost project in a file manager such as Gnome Commander.  

[COLOR=DarkSlateBlue]**sudo apt-get install gnome-commander**[/COLOR]

This allows php files to be edited (F3 or F4) and previewed in localhost.

---

### Post by DeathShot on 2012-02-29
> **dragonfly41 said:**
> Just a note to explain the logic of the last post  ..

The content of your php5.conf contains this ..

<IfModule mod_userdir.c>
<Directory[COLOR=Red] /home/*/public_html[/COLOR]>
 php_admin_value engine Off
</Directory>
</IfModule>


and that is why I thought you had your web content in your /home folder rather than your /root folder .. the default in /root is in fact /var/www

In my own setup I have ubuntu installed across two partitions ..  /root and /home partitions .. so my apache/php5 web content is not deleted when I have to reinstall ubuntu.

The link I posted above explains DocumentRoot.

If you prefer to keep your content in /var/www then you can reverse the change.

The issue you have is right clicking on your file in firefox to edit it.

Try installing Geany and then right click on your php files and open in Geany editor to edit the php file.

[COLOR=DarkSlateBlue]**sudo apt-get install geany**[/COLOR]

There are many other php editors you can try.   
You could setup a localhost project in a file manager such as Gnome Commander.  

[COLOR=DarkSlateBlue]**sudo apt-get install gnome-commander**[/COLOR]

This allows php files to be edited (F3 or F4) and previewed in localhost.

 Thanks, I will try this. It will certainly take getting used to but then again what doesn't :) Should I mark this thread as solved now?

---

### Post by dragonfly41 on 2012-02-29
At the risk of adding further options I forgot to mention

Komodo free editor

[http://www.activestate.com/komodo-edit](http://www.activestate.com/komodo-edit)

(n.b. not to be confused with the Komodo IDE which comes with a hefty price tag)

This _free_ editor allows your php content to be edited and previewed in one GUI.

So again download the free editor and in project > properties you can map URI's

e.g. [http://localhost](http://localhost)
mapped to
/var/www/

---

