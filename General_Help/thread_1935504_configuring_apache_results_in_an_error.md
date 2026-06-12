---
title: "configuring apache results in an error"
date: 2012-03-04
forum: General Help
---

### Post by kishon on 2012-03-04
I get apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName when I install apache2 in ubuntu. 

And hostname -f and hostname gives the same name. Looks like I dont have a fully configured name for my host. Is there a way to do it??

---

### Post by wojox on 2012-03-04
Try this:
```
gksudo gedit /etc/apache2/httpd.conf
```

Add this to the file:
```
ServerName localhost
```

Restart Apache2
```
sudo service apache restart
```

---

