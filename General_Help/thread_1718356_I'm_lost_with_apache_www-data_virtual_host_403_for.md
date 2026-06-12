---
title: "I'm lost with apache www-data virtual host 403 forbidden"
date: 2011-03-31
forum: General Help
---

### Post by RussellEngland on 2011-03-31
I'm lost :( I can't get past the 403 forbidden error

I have a directory /home/russ/public_html with a single index.html file
[HTML]
<html>
  <body>
    <h1>Success! It works! yey!</h1>
  </body>
</html>
[/HTML]From a terminal I've run

```

sudo chgrp -R www-data public_html
sudo chmod -R g+rwx public_html
ls -l
drwxrwxrwx   2 russ www-data    4096 2011-02-10 09:31 public_html
ls -l public_html
-rwxrwxrwx 1 russ www-data 309 2011-02-10 09:31 index.html

```I've edited the /etc/apache2/sites-enabled/000-default file
```

gksudo gedit /etc/apache2/sites-enabled/000-default

```Added my /home/russ/public_html directory
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
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

    Alias /russ/ "/home/russ/public_html"
    <Directory "/home/russ/public_html">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>


</VirtualHost>

```Restarted apache
```

sudo apachectl -k graceful

```Gone to [http://localhost/russ/index.htm](http://localhost/russ/index.htm)

but get a 403 forbidden error

After the restart, the contents of /var/log/apache2/error.log are:
```

[Thu Mar 31 12:24:32 2011] [notice] Graceful restart requested, doing restart
PHP Warning:  Module 'xdebug' already loaded in Unknown on line 0
[Thu Mar 31 12:24:32 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Mar 31 12:24:37 2011] [error] [client 127.0.0.1] (13)Permission denied: access to /russ/index.htm denied

```The contents of /var/www/.htaccess are (although I'm not sure when this happened)
```

Options +FollowSymLinks +ExecCGI

<IfModule mod_rewrite.c>
  RewriteEngine On

  # uncomment the following line, if you are having trouble
  # getting no_script_name to work
  # RewriteBase /

  # we skip all files with .something
  #RewriteCond %{REQUEST_URI} \..+$
  #RewriteCond %{REQUEST_URI} !\.html$
  #RewriteRule .* - [L]

  # we check if the .html version is here (caching)
  RewriteRule ^$ index.html [QSA]
  RewriteRule ^([^.]+)$ $1.html [QSA]
  RewriteCond %{REQUEST_FILENAME} !-f

  # no, so we redirect to our front web controller
  RewriteRule ^(.*)$ index.php [QSA,L]
</IfModule>

```Any idea what I'm missing?

---

### Post by RussellEngland on 2011-04-05
Yey! Finally got it to work...

I needed to give read permissions to the www-data group for /home and /home/russ

Not sure how to do that from the terminal, so ran
```
gksudo nautilus
```Then right click folder, select properties -> permissions

Select www-data from the group and change to access files


I got an "Oops! This link appears to be broken" message - so checked the apache error log and realised the virtual directory needed an / at the end :
```

    Alias /russ/ "/home/russ/public_html/"
    <Directory "/home/russ/public_html/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

```

Working fine now :)

---

### Post by deathadder on 2011-04-05
What are the permissions on the parent directories? So /home and /home/russ

You'll probably find that the www-data group doesn't have execute on /home/russ...

---

### Post by RussellEngland on 2011-04-05
Sorry deathadder - I didn't see your message - that was the solution :)

Cheers, Russ

---

