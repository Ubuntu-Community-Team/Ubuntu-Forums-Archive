---
title: "php statements not processed"
date: 2009-07-11
forum: General Help
---

### Post by chettiyar on 2009-07-11
My php codes in html file are not processed.  All the items inside <html> and </html> except those within <php and ?> are processed.  No error message also shown.  Can anybody help???
I get the following error message when I try to restart apache.
apache2: Could not reliably determine the server's fully qualified domain name, using XXX.X.X.X for ServerName
(in the place of X digits appear)

---

### Post by miklcct on 2009-07-13
Have you installed php5 ?

---

### Post by ELD on 2009-07-13
You will need to make sure you have installed php along side apache.

Heres a good way to do it:
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by JohnLau on 2009-07-13
Simply [click here to install php5]("apt:php5") package then restart apache by
```
sudo /etc/init.d/apache2 restart
```

---

### Post by Celauran on 2009-07-13
> **chettiyar said:**
> 
I get the following error message when I try to restart apache.
apache2: Could not reliably determine the server's fully qualified domain name, using XXX.X.X.X for ServerName
(in the place of X digits appear)

This is unrelated to the PHP problem. You can fix this by creating /etc/apache2/conf.d/fqdn containing the following line:

```
ServerName 127.0.0.1
```

---

