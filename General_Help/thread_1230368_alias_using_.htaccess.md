---
title: "alias using .htaccess"
date: 2009-08-03
forum: General Help
---

### Post by rolodoom on 2009-08-03
Hello. I installed LAMP-Ubuntu to use it as main server for our lan. So, I installed joomla, and it's working ok.

I'm wondering if I can change an url addres for a shorter one using .htaccess, I guess it is possible but haven't found a way. i.e: I want to make like an alias or something for an address like this **[http://mydomain/mycms/index.php?option=xxxx](http://mydomain/mycms/index.php?option=xxxx)** to look something like this **[http://mydomain/mycustomname](http://mydomain/mycustomname)**

thanks

---

### Post by cdenley on 2009-08-03
Just make a file like this:

/var/www/mycustomname/index.php
[PHP]
<?php
header('Location: ../mycms/index.php?option=xxxxx');
?>
[/PHP]

---

### Post by mcduck on 2009-08-03
Sure. First you need to make sure you have enabled using the .htaccess in your apache configuration for that site. Edit the site's setting file in /etc/apache2/sites-available and make sure you have set "AllowOverride all" for your site's rot directory.

Then just create the .htaccess file, and add your rewrite rules there.
```

RewriteEngine on

RewriteRule ^mycustomname$ index.php?option=xxxx [L]
```

---

