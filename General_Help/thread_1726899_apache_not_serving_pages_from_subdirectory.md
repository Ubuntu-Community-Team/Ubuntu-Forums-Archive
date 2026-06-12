---
title: "apache not serving pages from subdirectory"
date: 2011-04-11
forum: General Help
---

### Post by bjk03 on 2011-04-11
I have Joomla installed at /var/www/joomla, if I navigate to [http://localhost/joomla](http://localhost/joomla), I get a 404 error, but if I add index.php, the page loads. What is wrong?? Also I am not able to navigate to the administration part of Joomla for the same reason, typing in index.php doesn't load it in this case. Yes I have verified that all files are present in the directory. 

This is on 10.04.

---

### Post by maomoa on 2011-04-11
Add an .htaccess file to the directory with the following line:

DirectoryIndex index.php

---

### Post by bjk03 on 2011-04-11
I have added an .htaccess and still no change.

---

### Post by pqwoerituytrueiwoq on 2011-04-11
check the permissions on the file/folder
apache (www-data) will need read access at the very least

---

### Post by bjk03 on 2011-04-12
File permissions are 644, folders are 755. One thing I did see is that my user (bjk) is the owner of the joomla foler, does www-data need to own it?

---

### Post by SeijiSensei on 2011-04-12
.htaccess files are disallowed by default in the definition in /etc/apache2/sites-enabled/000-default:

```

       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                **AllowOverride None**
                Order allow,deny
                allow from all
        </Directory>

```

You can edit this file as root with sudo and add the DirectoryIndex directive there:

```

       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                **DirectoryIndex index.php**
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

or you can change AllowOverride from "None" to "All" to permit .htaccess to override the definition.  A safer approach is to choose from among the options as described [here]("http://httpd.apache.org/docs/current/mod/core.html#allowoverride").

---

### Post by bjk03 on 2011-04-12
> **SeijiSensei said:**
> .

You can edit this file as root with sudo and add the DirectoryIndex directive there:

```

       <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                **DirectoryIndex index.php**
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

I have made this change and still unable to get pages to display unless I type in index.php. I also have restarted my system (and thus Apache)and still no change! GRR!!

---

### Post by bjk03 on 2011-04-12
GOT IT FINALLY!!!!

Here is what I added to /etc/apache2/sites-svailable/default

```
<Directory /var/www/Joomla161/>
                Options Indexes FollowSymLinks MultiViews
                DirectoryIndex index.php
                RewriteBase /Joomla161
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
```

Once I added the RewriteBase line, things work as they should!!

---

