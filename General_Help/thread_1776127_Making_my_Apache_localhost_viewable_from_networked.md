---
title: "Making my Apache localhost viewable from networked machine"
date: 2011-06-05
forum: General Help
---

### Post by zanzibarwinds on 2011-06-05
Hi

My new ubuntu machine is my main PC now for dev work and is linked via ethernet to my other Vista machine which is simply a internet connection sharing PC.

I have the ubuntu machine setup with LAMP and do all my development and viewthe sites using [http://localhost](http://localhost) without issue.

Prolbem is I need to check the site in IE and thought the easiest way would be to view it from the VISTA machine but no amount of fiddling with it is letting me view the site.

I can see the ubuntu machine in my vista network area though but putting in [http://john-ubunutu/afrisa/](http://john-ubunutu/afrisa/) comes up with nothing.

Putting in the IP of the ubuntu box does nothing as well.

Do I need to edit the hosts file for this to work?

Regards and thanks
John

---

### Post by pqwoerituytrueiwoq on 2011-06-05
/etc/apache2/sites-available/default
should have something like this:
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
```if the ubuntu box is behind a router
ex:
router/modum
--vista box
--router
----ubuntu box
you will need to forward port 80

---

### Post by zanzibarwinds on 2011-06-05
Hi and thanks Pqw

I am missing references within the available sites folder. Added and all popped into place.

Thanks again.
John

---

### Post by pqwoerituytrueiwoq on 2011-06-05
so did that get it?

---

