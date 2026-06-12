---
title: "Lucid lamp-server: Apache can't handle *.php files"
date: 2010-06-15
forum: General Help
---

### Post by cb951303 on 2010-06-15
It's a rather common problem but none of the existing solutions seem to work.

I installed the lamp-server on a clean Ubuntu 10.04 system with:
```
sudo tasksel install lamp-server 
```
In previous versions of ubuntu this was all I had to do in order to have a working lamp setup.
This time when I try to view "index.php", browser downloads the file.

PHP5 module is enabled and here is the php5.conf file:
```

<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
	SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
	SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>

```

I also tried to add the lines below:
```

AddType application/x-httpd-php .php
AddType application/x-httpd-php .phtml

```
which looks like the way to fix this problem (from old threads) but it didn't work. Note that I restarted the apache server every time I made a change to the config files.

Anyone having this problem in Lucid?

---

### Post by cb951303 on 2010-06-15
I've just realized that the problem occurs only when using UserDir module.

I have no problem when running scripts from /var/www instead of /home/user_name/pbulic_html

Any ideas?

---

### Post by jjacozin on 2010-06-16
I'm having this exactly same problem! If you discovery to solve, tell me... I tried to solve by the many ways without success... If I get good result I'll tell you.

---

### Post by jrolland on 2010-07-16
Found the solution:

[https://wiki.ubuntu.com/UserDirectoryPHP](https://wiki.ubuntu.com/UserDirectoryPHP)

(Please mark this thread as "Solved", if you would be so kind.)

---

