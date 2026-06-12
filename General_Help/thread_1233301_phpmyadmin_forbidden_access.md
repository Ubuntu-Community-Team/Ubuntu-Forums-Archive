---
title: "phpmyadmin forbidden access"
date: 2009-08-06
forum: General Help
---

### Post by sphynk on 2009-08-06
Hi. Please try to avoid pointing and laughing I am brand new to Linux. Trying to change over completely from MS. Have managed to set up LAMP environment, but when I try [http://localhost/phpmyadmin](http://localhost/phpmyadmin) I am told 403 Forbidden. I've googled this a lot today, but no answers seem to help.

thanks in advance.

---

### Post by wojox on 2009-08-06
Open a terminal:
```
gksudo gedit /etc/apache2/apache2.conf
```

Then add this to bottom of file:
```
Include /etc/phpmyadmin/apache.conf
```
Save and Quit

```
sudo /etc/init.d/apache2 restart
```

---

### Post by sphynk on 2009-08-06
Thanks very much that did it.

---

