---
title: "Apache"
date: 2010-08-20
forum: General Help
---

### Post by tee_snipes on 2010-08-20
What is the proper command to run Apache? i'm using: 
/usr/local/apache2/bin/apachectl -f /usr/local/apache2/conf/httpd.conf but i keep getting this long *** error message.

---

### Post by WorMzy on 2010-08-20
```
sudo /etc/init.d/apache start
```

IIRC.

Might be

```
sudo service apache start
```


nowadays.

Replace start with "stop" or "restart" to suit your purpose.

---

