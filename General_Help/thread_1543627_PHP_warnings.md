---
title: "PHP warnings"
date: 2010-08-01
forum: General Help
---

### Post by shashanksingh on 2010-08-01
I have installed the php5 package but when I run my php code I do not get warnings, so its a bit difficult to debug (I get them when I use Xampp in windows)...
Do I need to install some other libraries/packages for that???

---

### Post by WorMzy on 2010-08-01
You just need to modify your config, then restart apache.

The file you need to modify to enable error messages is /etc/php5/apache2/php.ini, edit it with
```
gksu gedit /etc/php5/apache2/php.ini
```

The variable you want to search for is "display_errors", switch it from "Off" to "On", then run
```
sudo service apache restart
```

---

### Post by shashanksingh on 2010-08-02
Thank you..
It Works...
:)

---

