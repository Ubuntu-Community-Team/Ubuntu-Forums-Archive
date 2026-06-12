---
title: "MySQL Connect issue"
date: 2010-09-20
forum: General Help
---

### Post by U2XS on 2010-09-20
I used the [Bluecherry Zoneminder Live CD]("http://sourceforge.net/projects/zoneminder-cd/") to install the Zoneminder surveillance system.  Everything work until I misguidedly tried to change the password using PHPMyAdmin.  ZM had a hashed password which I attempted to change to "ABC".  Now I can't remember that string of characters and my zoneminder control panel will not load.  Does anyone know how to recreate the name?  Or to pass the PW value "ABC" so that it will work?  Thanks


**The error message is:**```

Warning: mysql_pconnect() [function.mysql-pconnect]: Access denied for user 'zm'@'localhost' (using password: YES) in /var/www/includes/database.php on line 32
Could not connect to database: Access denied for user 'zm'@'localhost' (using password: YES)
```

---

