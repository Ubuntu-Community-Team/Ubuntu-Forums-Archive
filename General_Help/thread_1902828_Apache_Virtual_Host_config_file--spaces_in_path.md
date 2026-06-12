---
title: "Apache Virtual Host config file--spaces in path"
date: 2011-12-31
forum: General Help
---

### Post by javaman90 on 2011-12-31
Hi,
I followed the directions [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") for setting up Apache, PHP, and MySQL. I attempted creating a virtual host with a root directory that has a path with spaces; yet I get 403 Forbidden errors when trying to access the localhost. In addition, Apache won't even create the "index.html" file on the fly for this site. 

I then tried creating another site with a root directory whose path has no spaces; and Apache and PHP work fine. The index.html file is created on the fly as well. 

Here is my config code for the site [that won't work:]("http://pastebin.com/raw.php?i=HEZU9G9p")
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot "/home/vance/Aptana Studio 3 Workspace/TestingSpacesPHP"
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory "/home/vance/Aptana Studio 3 Workspace/TestingSpacesPHP">
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
```Here is the code for the [site that works:]("http://pastebin.com/raw.php?i=irsKVqFi")

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/vance/learningphp
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/vance/learningphp>
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
```Both config files are identical except for the paths in the <Directory> entry and the path for the document root.

Also, when I restart the Apache server enabled with the site that gives 403 replies; no errors are displayed in the console. 
I am using Ubuntu 10.10.
Thanks for any help,
Vance

---

### Post by satanselbow on 2012-01-01
Only a guess and not tried it in practice but you could try substituting the spaces in your <Directory> line with either "%20" or "\040" - without the quotes ;)

---

### Post by javaman90 on 2012-01-01
Thanks for the suggestion, but that didn't work. On restarting Apache, it complains about the Document Root not existing. 

Vance

---

