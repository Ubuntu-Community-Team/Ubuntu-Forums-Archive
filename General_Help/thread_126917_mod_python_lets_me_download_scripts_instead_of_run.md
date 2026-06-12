---
title: "mod_python lets me download scripts instead of running them"
date: 2006-02-07
forum: General Help
---

### Post by Lews Therin on 2006-02-07
I'm trying to get mod_python working, but can't get it to run the scripts instead of letting me download them. The server config options seem to be the same as those in my Gentoo box, which works fine.

This 000-default config file. I added the mod_python bits in the middle
```
<VirtualHost *>
  ServerAdmin [my email]

  DocumentRoot /var/www/localhost/htdocs
  <Directory />
    Options FollowSymLinks
    AllowOverride None
  </Directory>
  <Directory /var/www/localhost/htdocs>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
    # This directive allows us to have apache2's default start page
      # in /apache2-default/, but still have / go to the right place
      # Commented out for Ubuntu
      #RedirectMatch ^/$ /apache2-default/

    # Enable mod_python
    <IfModule mod_python.c>
      AddHandler    mod_python .py
      PythonHandler mod_python.publisher
      PythonDebug   On
    </IfModule>
  </Directory>

  ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
  <Directory "/usr/lib/cgi-bin">
    AllowOverride None
    Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Order allow,deny
    Allow from all
  </Directory>

  ErrorLog /var/log/apache2/error.log

  # Possible values include: debug, info, notice, warn, error, crit,
  # alert, emerg.
  LogLevel warn

  CustomLog /var/log/apache2/access.log combined
  ServerSignature On

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

