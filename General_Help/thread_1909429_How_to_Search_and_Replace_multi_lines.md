---
title: "How to Search and Replace multi lines?"
date: 2012-01-15
forum: General Help
---

### Post by houmank on 2012-01-15
Hi,

I have a file like this

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
</VirtualHost>
```


I would like to achieve this:

```
<VirtualHost *:80>
        ServerAdmin info@domain.com
        ServerName domain.com
        ServerAlias www.domain.com
 
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
</VirtualHost>
```

I tired this but the line carriage doesn't work properly.
I even tried \r\n without luck.  

> sudo sed -i "s/webmaster@localhost/info@domain.com\rServerName domain.com \rServerAlias www.domain.com/" /etc/apache2/sites-available/domain

I get this weird character there between:

```
<VirtualHost _default_:443>
        ServerAdmin info@domain.com ^MServerName domain.com ^MServerAlias www.domain.com

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
</VirtualHost>
```

What am I missing? 

Many Thanks,

---

### Post by Paddy Landau on 2012-01-15
New-line is \n not \r. Try that.

---

