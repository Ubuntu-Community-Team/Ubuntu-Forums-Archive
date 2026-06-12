---
title: "phpMyadmin doesn't seem to work :("
date: 2011-03-17
forum: General Help
---

### Post by Woodknight on 2011-03-17
I recently installed LAMP using this handy guide:
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

Everything seams to work except phpMyadmin

I'm supposed to type [http://localhost/phpMyAdmin/](http://localhost/phpMyAdmin/) to use it but I get a 404 error "The requested URL /phpMyAdmin/ was not found on this server."

Thank you in advance. :)

---

### Post by mcduck on 2011-03-17
Have you restarted Apache after installing phpMyAdmin?

---

### Post by Woodknight on 2011-03-17
Yes, I restarted it a couple of times but nothing changed...

---

### Post by timgood on 2011-03-17
Try [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) (note the lowercase) which works on my box.
Hope this helps.

---

### Post by indytim on 2011-03-17
I suggest that you look in /var/www see if you have a folder /phpMyAdmin.  I think when phpMyAdmin is installed from the repository it plunks it in /etc with symbolic links back to /var/www (not 100% on this as I always install direct using the standard phpMyAdmin installation vs the repository version).

IndyTim / DataMan

---

### Post by Woodknight on 2011-03-17
Finally working! It appears the lower case did the trick. Thanks so much! :)

---

### Post by timgood on 2011-03-17
You're welcome! Perhaps you would like to mark this thread as solved!

---

### Post by r.osmanov on 2011-03-17
If you chose apache2 Web server during setup, phpMyAdmins configuration should be in /etc/phpmyadmin/apache.conf.
/etc/apache2/conf.d/phpmyadmin.conf is a link to /etc/phpmyadmin/apache.conf. The file declares a vhost in /usr/share/phpmyadmin folder:
```

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
    Options FollowSymLinks
    DirectoryIndex index.php

    <IfModule mod_php5.c>
        AddType application/x-httpd-php .php

        php_flag magic_quotes_gpc Off
        php_flag track_vars On
        php_flag register_globals Off
        php_value include_path .
    </IfModule>

</Directory>
...

```Since you should normally have it on [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/), look at links in /etc/apache2/sites-enabled/ folder. It should contain localhost. Here is mine:
```

$ ll /etc/apache2/sites-enabled/
total 12K
drwxr-xr-x 2 root root 4.0K 2011-03-17 21:46 ./
drwxr-xr-x 7 root root 4.0K 2010-12-21 13:33 ../
lrwxrwxrwx 1 root root   28 2011-03-17 21:46 localhost -> ../sites-available/localhost

```

EDIT: Oops, you fixed it already :)

---

