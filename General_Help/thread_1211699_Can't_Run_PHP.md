---
title: "Can't Run PHP"
date: 2009-07-12
forum: General Help
---

### Post by mthalis on 2009-07-12
I install apache2 using package manager. it works perfectly but if i try to run PHP file using apache2 server it always ask to save local disk(rrun using browser) instead of display output in browse.

---

### Post by darolu on 2009-07-12
Are your files under the default "www" directory or any other directory being monitored by apache?

---

### Post by ewankho on 2009-07-12
Isn't PHP a different module that needs to be installed seperately?

---

### Post by mthalis on 2009-07-12
Files locate under WWW directory, both install separately
> apache2
php5

---

### Post by darolu on 2009-07-13
Is the directory where your php files are in, included in your httpd.conf file?

---

### Post by mthalis on 2009-07-13
My all php files in www folder. Here is my default file setting, which is under /etc/apache/sites-available/
> 
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
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

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>  

---

### Post by mthalis on 2009-07-13
Any comments ...

---

### Post by nikhilk on 2009-07-13
Is your web server configured to correctly handle any of the following MIME types, application/x-php php php3 php4?
Also check if you have the correct AddHandler directive for handling php scripts?

---

### Post by mthalis on 2009-07-13
I can't exactly understand you're idea. Can you send more details..

---

### Post by ewankho on 2009-07-13
If you want to go straight to php programming without being bogged down by by apache/php/sysql configuration details you can just install [XAMPP]("http://www.apachefriends.org/en/index.html") for whatever OS you have.

---

### Post by nikhilk on 2009-07-13
> **mthalis said:**
> I can't exactly understand you're idea. Can you send more details..

Take a look at the sections on AddHandler Directive and AddType Directive in the Apache 2.0 documentation of [http://httpd.apache.org/docs/2.0/mod/mod_mime.html](mod_mime).

---

