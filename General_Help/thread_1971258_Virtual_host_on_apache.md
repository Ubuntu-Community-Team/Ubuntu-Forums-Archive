---
title: "Virtual host on apache"
date: 2012-05-02
forum: General Help
---

### Post by Chris Psycho on 2012-05-02
Hi guys. I'm having trouble setting up a virtual host on my pc (localhost).

I have pretty much a fresh install of apache/php5/mysql.

I have added a 'cms' file  to /etc/apache2/sites-available

Contents: ```
NameVirtualHost *:80

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName cms.dev
    DocumentRoot /var/www/cms

    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/cms/>
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

    ErrorLog ${APACHE_LNameVirtualHost *:80

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName cms.dev
    DocumentRoot /var/www/cms

    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/cms/>
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

    ErrorLog ${APACHE_LOG_DIR}/error_cms.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access_cms.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>OG_DIR}/error_cms.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access_cms.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```However when going to cms.dev in my browser it keeps showing the contents of /var/www and not /var/www/cms.

Any ideas? I have restarted apache and it's still not reflecting the new virtual host.

---

### Post by Cheesemill on 2012-05-02
Have you enabled the site?
```
sudo a2ensite cms
```
Then restart apache

---

### Post by Chris Psycho on 2012-05-02
> **Cheesemill said:**
> Have you enabled the site?
```
sudo a2ensite cms
```Then restart apache

Hurrah! :D that's solved it.

It did give me this error message however (after running the instructed 'sudo service apache2 reload')
[warn] NameVirtualHost *:80 has no VirtualHosts

Should I be concerned?

Thank you for your help :P

---

