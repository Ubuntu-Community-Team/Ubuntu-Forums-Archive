---
title: "can't visit my webpages folder locally"
date: 2010-01-04
forum: General Help
---

### Post by manuleka on 2010-01-04
ok my webserver is used locally for testing and learning purposes... 

now when i key the server ip on my 2nd pc it brings up the It Works default page (Apache2), but when i visit a subfolder which has wordpress-mu installed in i get a 403 forbidden error...

how to i enable myself to view this particular folder? 

here's the .htaccess file on the wordpress mu folder:
```

RewriteEngine On
RewriteBase /proj/manuscorner.co.cc/

#uploaded files
RewriteRule ^(.*/)?files/$ index.php [L]
RewriteCond %{REQUEST_URI} !.*wp-content/plugins.*
RewriteRule ^(.*/)?files/(.*) wp-content/blogs.php?file=$2 [L]

# add a trailing slash to /wp-admin
RewriteCond %{REQUEST_URI} ^.*/wp-admin$
RewriteRule ^(.+)$ $1/ [R=301,L]

RewriteCond %{REQUEST_FILENAME} -f [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule . - [L]
RewriteRule  ^([_0-9a-zA-Z-]+/)?(wp-.*) $2 [L]
RewriteRule  ^([_0-9a-zA-Z-]+/)?(.*\.php)$ $2 [L]
RewriteRule . index.php [L]

<IfModule mod_security.c>
<Files async-upload.php>
SecFilterEngine Off
SecFilterScanPOST Off
</Files>
</IfModule>

```

---

### Post by shairozan on 2010-01-04
Hey there, 

First off, we want to make sure that the directory you are accessing has permissions that are allowed. Best bet is change the ownership of the files to www-data. 

for example, for a directory called joomla in var/www, you would do the following

```
chown -R www-data:www-data /var/www/joomla
```

This makes sure apache can read the files. The second is to make sure that you have a site defined in the sites-enabled / sites-available file. What I would do in this kind of scenario is just setup a re-direct in the sites-available file. To do this, you would do the following:

(1) vi /etc/apache2/sites-enabled/000-default
(2) Insert the following before the last </ virtual host> tag
RedirectMatch ^/$ /joomla
(3) This would make sure any queries sent to the main server address would be forwarded to the directory of choice, in this case, /joomla. Apache will then look for an index.* file. 

Hopefully some of this will be useful. You have a lot more experience with the re-write engine than I do.

---

