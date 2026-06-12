---
title: "apache2 subdirectories"
date: 2009-08-05
forum: General Help
---

### Post by flagitude on 2009-08-05
hello, im trying to get apache2 to allow me to access subdirectories and files in those subdirectories in the default directory
 
what i have set up is an internal website which allows any file to be downloaded from the default directory:
 
/var/STOREPOINT
 
now i can download any file in that directory but if i try to access any folder in that directory i get a 403 permission denied. the same goes for files in that directory.
 
Also the folder i try to access in the default directory is hidden...
 
any new folders created gives me a 403 error.
 
any ideas on how to fix this - thanks!

---

### Post by Glyndwr on 2009-08-05
what is your document root set to ?

---

### Post by flagitude on 2009-08-05
well this is whats in my /etc/apache2/sites-available/default
 
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/STOREPOINT/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/STOREPOINT>
                Options Indexes FollowSymLinks +ExecCGI
                AllowOverride AuthConfig FileInfo
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

```

---

