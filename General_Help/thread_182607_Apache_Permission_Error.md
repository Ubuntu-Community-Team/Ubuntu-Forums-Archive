---
title: "Apache Permission Error"
date: 2006-05-26
forum: General Help
---

### Post by mesh2005 on 2006-05-26
I tried to request a web page on my localhost but I got the following error
Forbidden

You don't have permission to access /shop/personnel/home.php on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.0.54 (Ubuntu) PHP/4.4.0-3ubuntu2 Server at localhost Port 80

---

### Post by ifokkema on 2006-05-26
Hi,

Did you make sure the directory is readable for the www-data user? (Maybe a stupid question...)

Ivo

---

### Post by cskeide on 2006-05-26
Is the file readable by all users?```
sudo chmod +r home.php
sudo chown www-data:www-data home.php
```

---

### Post by mesh2005 on 2006-06-06
Thanks!

---

