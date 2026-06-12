---
title: "Apache Issue"
date: 2009-12-06
forum: General Help
---

### Post by lewisforlife on 2009-12-06
I am having a strange issue with Apache2/PHP.  I installed it with:

```
sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart

```

I created a file, 'index.php' in /var/www.  When I go to 'http://localhost' in my web browser, I get prompted to download a file, I downloaded the file which is named 'uO5p+4ZS.phtml.part', and it contains the code that is in my index.php file.  If I go to [http://localhost/index.php](http://localhost/index.php), my page is displayed correctly.  I have tried multiple times restarting the apache server, but this does not fix the problem.

---

### Post by fragos on 2009-12-06
You need to tell Apache to use the PHP you installed. Open /etc/apache2/.
Edit or create httpd.conf to include the following three lines:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

### Post by lewisforlife on 2009-12-06
That did the trick.

Thanks,

---

