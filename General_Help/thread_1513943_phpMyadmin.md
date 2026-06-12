---
title: "phpMyadmin"
date: 2010-06-20
forum: General Help
---

### Post by miko5054 on 2010-06-20
im receiving  this error 
```
Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.
```

id tried this solution but the file is empty..
[HTML]http://www.webteches.com/cannot-start-session-without-errors-please-check-errors-given-in-your-php-andor-webserver-log-file-and-configure-your-php-installation-properly/[/HTML]


thanks

---

### Post by bruno9779 on 2010-06-20
Are you running into these errors just after install, or has it been working before?

---

### Post by wojox on 2010-06-20
Have you tried this? [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Phpmyadmin%20&%20mysql-admin](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Phpmyadmin%20&%20mysql-admin)

---

### Post by miko5054 on 2010-06-20
it worked copel of days now ,when im tring to restat apache2 im geting this error 

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start

```

---

### Post by wojox on 2010-06-20
Try adding this to apache2.conf

ServerName "YourSite.com" Change YourSite to your domain name.

Restart apache.

---

### Post by miko5054 on 2010-06-21
i run this code ```
gksudo "gedit /etc/apache2/apache2.conf"

```

but there isn't  any 
```

ServerName "YourSite.com" Change YourSite to your domain name.
```

????

---

