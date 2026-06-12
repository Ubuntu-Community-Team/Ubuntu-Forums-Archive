---
title: "Cannot get Apache to invoke PHP"
date: 2012-05-24
forum: General Help
---

### Post by jcobban on 2012-05-24
I have installed Apache and PHP5:
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo service apache2 restart

But when I browse to a .php file I get the .php file, not the result of running PHP on it.  That is the browser asks me what application to use to view a .php file.

/etc/apache2/sites-enabled/000default is:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/jcobban/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/jcobban/public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

---

### Post by roelforg on 2012-05-24
Make sure the php-code starts with
```

<?php

```
Because php5 will only act upon code between <?php and ?>
 
EDIT:
Let me explain by example:
Say the php file is this:
```

echo "Hello world!<br/>";

```
if so, then php will output the code.
This one does as wanted:
```

**<?php**
echo "Hello world!</br>";
**?>**

```
this one outputs hello world

---

### Post by skater40165 on 2012-05-24
Try 

```
sudo a2enmod php5
sudo service apache2 restart

```

---

### Post by maverickaddicted on 2012-05-24
After enabling php5 module, you can check it by running -

```
sudo apache2ctl -M
```

---

### Post by SeijiSensei on 2012-05-24
Check that the files /etc/apache2/mods-available/php5.conf and php5.load exist.  If they're not there, install the libapache2-mod-php5 package.

---

### Post by jcobban on 2012-05-24
> **roelforg said:**
> Make sure the php-code starts with
```

<?php

```
Because php5 will only act upon code between <?php and ?>
 


This is an existing web site that I am merely moving to a new computer.

---

### Post by jcobban on 2012-05-24
> **skater40165 said:**
> Try 

```
sudo a2enmod php5
sudo service apache2 restart

```

The output to the enable mod command is:

```
sudo a2enmod php5
Module php5 already enabled
```

---

### Post by jcobban on 2012-05-24
> **maverickaddicted said:**
> After enabling php5 module, you can check it by running -

```
sudo apache2ctl -M
```

The output from this command is:

```
sudo apache2ctl -M
[sudo] password for jcobban: 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 jk_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 reqtimeout_module (shared)
 setenvif_module (shared)
 status_module (shared)
 userdir_module (shared)
Syntax OK

```

---

### Post by roelforg on 2012-05-24
> **jcobban said:**
> The output from this command is:

```
sudo apache2ctl -M
[sudo] password for jcobban: 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 jk_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 reqtimeout_module (shared)
 setenvif_module (shared)
 status_module (shared)
 userdir_module (shared)
Syntax OK

```

Read my previous post.

---

### Post by jcobban on 2012-05-24
> **SeijiSensei said:**
> Check that the files /etc/apache2/mods-available/php5.conf and php5.load exist.  If they're not there, install the libapache2-mod-php5 package.

The files are there:

```
ls /etc/apache2/mods-available/php5.*
/etc/apache2/mods-available/php5.conf  /etc/apache2/mods-available/php5.load
```

---

### Post by roelforg on 2012-05-24
> **jcobban said:**
> The files are there:

```
ls /etc/apache2/mods-available/php5.*
/etc/apache2/mods-available/php5.conf  /etc/apache2/mods-available/php5.load
```

Am i the only one here that thinks the problem is that php will only run php-code inside <?php and ?> tags and that those tags are missing from the file?

---

### Post by jcobban on 2012-05-24
> **roelforg said:**
> Read my previous post.

I don't understand.  As I said in response to your previous post this is an existing web-site with hundreds of pages of PHP code that is already running on two development computers and a production site [www.jamescobban.net]("http://www.jamescobban.net").  This is not a matter of a syntax error in a single PHP page.

---

### Post by roelforg on 2012-05-24
> **jcobban said:**
> I don't understand.  As I said in response to your previous post this is an existing web-site with hundreds of pages of PHP code that is already running on two development computers and a production site [www.jamescobban.net]("http://www.jamescobban.net").  This is not a matter of a syntax error in a single PHP page.

Sorry, i missed that post. :oops:
If it's any help, here's my 000-defaults, it runs phpfiles fine so maybe it'll help.
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options +ExecCGI Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by jcobban on 2012-05-24
> **roelforg said:**
> Am i the only one here that thinks the problem is that php will only run php-code inside <?php and ?> tags and that those tags are missing from the file?

OK if you won't believe me, of course one of the hundreds of pages of PHP code on my site is the standard phpinfo script:

[HTML]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<html>
<head>
	<title>Test PHP</title>
	<META HTTP-EQUIV="CONTENT-TYPE" CONTENT="text/html; charset=UTF-8">
	<META NAME="CREATED" CONTENT="20060124;11200221">
	<META NAME="Author" CONTENT="James Cobban">
	<link rel="stylesheet" type="text/css" href="styles.css"/>
<!-- Copyright James Cobban 2009 -->
</head>
<body LANG="en-US" DIR="LTR">
<h1>Test PHP</h1>
<?php print_r(phpinfo()); ?>
</body>
</html>
[/HTML]

If I make a typo, such as you are suggesting, then I get incorrect output or a syntax error out of the PHP interpreter.  For example I have just mangled [www.jamescobban.net/phpinfo.php]("http://www.jamescobban.net/phpinfo.php").  That is not what I am getting.  The browser is asking me what program I want to use to look at files of type ".php", so Apache is not invoking the PHP interpreter.

---

### Post by jcobban on 2012-05-24
> **roelforg said:**
> Sorry, i missed that post. :oops:
If it's any help, here's my 000-defaults, it runs phpfiles fine so maybe it'll help.


When I have that sort of 000-default file my development machine works fine.  It is because the major difference between my new development machine and the one I am installing is the 000-defaults file that I included it in my original post.  The issue is that I want my development host to look as much as possible like my production site.  On my production site, which of course I do not administer, the web site is in /home/jcobban/public_html, not in /var/www.  I have a bunch of kluges in the web site code to deal with the fact that the URL on the development machine has a different structure from that on the production machine.

The only things I changed in the 000-defaults file is the two references to /var/www.  I have looked over the php.ini file and I cannot see anything that I should modify there in order to get this to work.

I know I have to be doing something stupid to be causing this problem, but I am not a LAMP guru despite years of web development.  I just want to code services, not muck around in the management of the server software.

---

### Post by wojox on 2012-05-24
```
<?php
print_r (phpinfo());
?>

```

Place that in a file call it phpinfo.php and place it in DocRoot and run it.

---

### Post by jcobban on 2012-05-24
> **wojox said:**
> ```
<?php
print_r (phpinfo());
?>

```

Place that in a file call it phpinfo.php and place it in DocRoot and run it.

It doesn't run!  Of course I have a phpinfo.php page on my site.  But it is not executed.  Why will no one believe me?

---

### Post by wojox on 2012-05-24
We believe you. :P

I've never used print_r. The only info I see is to pass it a varable not a function. :confused:

What about the standard:
[PHP]<?php
phpinfo();
?>[/PHP]

Are you porting this from another *nix server?

---

### Post by maverickaddicted on 2012-05-24
Can you add following code in your httpd.conf file -

```

$ sudo nano /etc/apache2/httpd.conf

LoadModule php5_module modules/libphp5.so
AddHandler php5-script php 
DirectoryIndex index.html index.php
AddType text/html php


```

```

$sudo service apache2 force-reload

```

---

### Post by wojox on 2012-05-24
It works now. :)

```
/home/jcobban/public_html/php.ini 
```

---

### Post by maverickaddicted on 2012-05-24
> **wojox said:**
> It works now. :)

```
/home/jcobban/public_html/php.ini 
```

Can you explain what you did? I want to know, it will help.

---

### Post by jcobban on 2012-05-24
> **wojox said:**
> It works now. :)

```
/home/jcobban/public_html/php.ini 
```

Yes, it works on every other machine I have it deployed on.  I just don't understand what I am doing wrong so that it doesn't work on this system.

---

### Post by wojox on 2012-05-24
> **jcobban said:**
> Yes, it works on every other machine I have it deployed on.  I just don't understand what I am doing wrong so that it doesn't work on this system.

So you have other Ubuntu servers running these scripts?

---

### Post by wojox on 2012-05-24
> **maverickaddicted said:**
> Can you explain what you did? I want to know, it will help.

I just clicked his link [he posted]("http://www.jamescobban.net/phpinfo.php") and php was parsed.

---

### Post by jcobban on 2012-05-24
> **wojox said:**
> So you have other Ubuntu servers running these scripts?

Yes.  In particular my public web-site [www.jamescobban.net]("http://www.jamescobban.net").  For example [phpinfo.php]("http://www.jamescobban.net/phpinfo.php")

---

### Post by jcobban on 2012-05-24
> **wojox said:**
> I just clicked his link [he posted]("http://www.jamescobban.net/phpinfo.php") and php was parsed.

Yes but that is my production site.  It is my private development site that I cannot get to work ever since moving it from my broken laptop to a new machine.

---

### Post by dragonfly41 on 2012-05-24
Is it perhaps too obvious to check permissions in public_html?    /home/jcobban/public_html/   and to reload browser each time .. Ctrl+F5

---

### Post by skater40165 on 2012-05-24
Not o sound like a windows user but if I remember correctly after I had my web server set up I had to reboot before I could get php files to load just a thought. Sorry it's been a while since I tried enabling php.

---

### Post by jcobban on 2012-05-24
> **dragonfly41 said:**
> Is it perhaps too obvious to check permissions in public_html?    /home/jcobban/public_html/   and to reload browser each time .. Ctrl+F5

If the permissions were wrong I would get a 403 error and I couldn't access any pages.  I am actually able to access the php pages, but they are presented to my browser as text/php instead of text/html.

---

### Post by jcobban on 2012-05-24
> **skater40165 said:**
> Not o sound like a windows user but if I remember correctly after I had my web server set up I had to reboot before I could get php files to load just a thought. Sorry it's been a while since I tried enabling php.

I have rebooted several times during this exercise.

---

### Post by SeijiSensei on 2012-05-25
> /home/jcobban/public_html/php.ini

What is this file?  The standard location for php.ini is /etc/php5/apache2/php.ini.  This file will be ignored in a standard installation.

Also home directories have 700 permissions by default so the www-data user that Apache runs as can't see anything in a home directory unless you've changed the permissions accordingly.  At a minimum the directory /home/jcobban needs to have 711 permissions.  

Just because your hosting company uses the public_html directory for customers' sites doesn't mean the same configuration will work for you.  I'd start by fixing permissions in /home/jcobban and see if that helps.

If you place pure HTML files in the same directory as the PHP scripts, can you see those files?  If not, the problem is permissions, not PHP.

---

### Post by jcobban on 2012-05-27
> **jcobban said:**
> Yes, it works on every other machine I have it deployed on.  I just don't understand what I am doing wrong so that it doesn't work on this system.
I gave up trying to fix the problem, uninstalled everything and reinstalled from scratch using tasksel.  Everything works fine now.

---

