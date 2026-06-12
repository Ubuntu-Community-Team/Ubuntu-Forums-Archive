---
title: "Installed PHP Apache &amp; MySQl"
date: 2009-07-15
forum: General Help
---

### Post by ssdt on 2009-07-15
I have installed PHP Apache and MySQL in ubuntu. now i am trying to use it but doesn't work out in localhost becaue it says "[SIZE="5"]IT WORKS![/SIZE] in big fonts like this. How do i make my file come up and where do i have to keep my files? if i cannot use it then can i uninstall it?

thanks

---

### Post by wojox on 2009-07-15
DocumentRoot is in /var/www/

---

### Post by cpetercarter on 2009-07-15
By default, the DocumentRoot is at /var/www/. Trouble is that /var/www/ is owned by root, so you have to use sudo anytime you want to place anything there, which is a pain if you are trying to develop a web application. It is often a good idea therefore to change the Document Root to somewhere in your home directory. The section on Virtual Hosts in [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") tells you how to do this.

---

### Post by csabo2 on 2009-07-15
on a side note, you may want to install webmin for easier management (if you're not familiar with apache)

---

### Post by Tibuda on 2009-07-15
> **cpetercarter said:**
> By default, the DocumentRoot is at /var/www/. Trouble is that /var/www/ is owned by root, so you have to use sudo anytime you want to place anything there, which is a pain if you are trying to develop a web application. It is often a good idea therefore to change the Document Root to somewhere in your home directory. The section on Virtual Hosts in [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") tells you how to do this.

You just have to change the owner to yourself. I usually do a "sudo chown $USER:$USER /var/www", but running Nautilus as root ("gksudo nautilus") and change the owner in the /var/www folder properties also works.

---

### Post by ssdt on 2009-07-15
then how do u move it to lets say my documents?

---

### Post by wojox on 2009-07-15
Here is the whole tutorial for setting it up:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Tibuda on 2009-07-15
> **ssdt said:**
> then how do u move it to lets say my documents?

Press Alt+F2, type **gksudo gedit /etc/apache2/sites-available/default**, enter your password, and change the directory path in this line to something else:
```
DocumentRoot /var/www
```

Then you need to restart the server, by restarting the computer or running:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by ssdt on 2009-07-15
Thank you. Topic solved

---

