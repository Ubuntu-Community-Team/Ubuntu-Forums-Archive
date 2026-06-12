---
title: "How can I run PHP in browser offline?"
date: 2010-04-20
forum: General Help
---

### Post by ayet on 2010-04-20
I cant seem to figure this out, any help?

---

### Post by mcduck on 2010-04-20
You can't run PHP in a web browser, you need a web server with PHP to execute the PHP code and create a HTML page for the browser.

If you want to, installing a LAMP server on Ubuntu is very easy, and that will of course allow you to run PHP pages on your local machine.

In a nuthshell: open a temrinal and run "sudo tasksel install lamp-server". This will install Apache, PHP and MySQL for you. You'll then find the server's configuration files in /etc/apache2/, the web root directory in /var/www/, and can access the web pages in your browser using address [http://localhost/](http://localhost/). You'll find more detailed information here: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by ayet on 2010-04-20
sorry for not telling all the details first, I can already run php,mysql,apache2 in my ubuntu but only when online or with a network connection,.
so how can i run this offline? how can i run php when my nic card is not conncted to anything?

when i type [http://localhost](http://localhost) it shows offline mode only no php output

---

### Post by mcduck on 2010-04-20
Just make sure that your web browser isn't set to offline mode, it might do that automatically if you aren't connected to any network.

For Firefox, the option is in File/Work Offline.

---

### Post by richardjennings on 2010-04-20
xampp

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

