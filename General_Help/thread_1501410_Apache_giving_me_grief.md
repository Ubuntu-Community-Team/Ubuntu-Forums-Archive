---
title: "Apache giving me grief"
date: 2010-06-04
forum: General Help
---

### Post by J V on 2010-06-04
After installing phpmyadmin and using it to setup a database and user, apache is giving me grief... I've tried google, but none of the advice seems to work...

Edit: Ok, although I still believe it has something to do with the phpmyadmin installation, changing <VirtualHost *> to <VirtualHost 127.0.0.1:80> stopped the errors from occurring... Now I'm still getting a silent failure, the page just shows up blank...

```
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Jun 04 15:08:12 2010] [warn] NameVirtualHost 127.0.0.1:80 has no VirtualHosts
```My 000-default"
```
NameVirtualHost *
<VirtualHost *>
    ServerAdmin webmaster@localhost
    
    DocumentRoot /home/j/www/

    <Directory /home/j/www>
        Options FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from 127.0.0.1
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

</VirtualHost>
```

---

### Post by J V on 2010-06-04
I'm trying to build a very interesting site, I'd like it to work please...

Does anyone know what this could be?

---

