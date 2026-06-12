---
title: "Problems with running .php files"
date: 2011-05-23
forum: General Help
---

### Post by ankit.vader on 2011-05-23
I've recently started learning PHP. Now, while the CLI-PHP works fine, I cannot run CGI-PHP files in browser. I get following error whenever I run .php file in browser

```

Forbidden
You don't have permission to access /sample002.phtml on this server.

```

this is the configuration of my "/etc/apache2/sites-available/default" file

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot "/home/ankit/Documents/Programming Stuff/PHP"

    <Directory "/home/ankit/Documents/Programming Stuff/PHP">
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory />
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

As you can see, I've changed DocumentRoot from /var/www to the path mentioned and after that the problem started. sample002.phtml file is also in the specified path. Is there a way to handle this error, or do I have to change DocumentRoot again?
I've searched a lot on google, I've also changed the permission of the file but it didn't work.
Any help is appreciated.

---

### Post by ankit.vader on 2011-05-23
bump

---

### Post by ankit.vader on 2011-05-23
never mind, I got it right, there was a problem of permission of parent folder.

---

