---
title: "https configuration on apache2 ubuntu 10.04"
date: 2010-12-27
forum: General Help
---

### Post by zohaib82 on 2010-12-27
Hi,

I have configure https for my local intranet on ubuntu.

I have followed following documentation.

[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

[https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html)

I am using Self-Signed Certificate.

I have 10 folders inside http://"myipaddress" location.I want to activate/access https:// for specific folder ([https://myipaddress/myfolder](https://myipaddress/myfolder)).

here https getting activated for whole apache2 server.How can i activate it for specific folder. 

Best Regards,
Zohaib.

---

### Post by zohaib82 on 2010-12-27
I have find one solution on following web url.

[http://www.vanemery.com/Linux/Apache/apache-SSL.html](http://www.vanemery.com/Linux/Apache/apache-SSL.html)

**Configure Apache to require client certificates for a specific directory:**

  In order to require client certificates for the /var/www/SSL/Certneeded directory, you will need to  add the following lines to the /etc/httpd/conf.d/ssl.conf configuration file:
  <Directory /var/www/SSL/Certneeded>
    SSLVerifyClient require
    SSLVerifyDepth 1
</Directory>


If i put this in /etc/httpd/conf.d/ssl.conf and /etc/apache2/sites-available/default
file then it will work https for "Certneeded" directory and other directory as http
This will work in ubuntu?

OR

.htaccess file change solution work as per following url.

[http://www.besthostratings.com/articles/force-ssl-htaccess.html](http://www.besthostratings.com/articles/force-ssl-htaccess.html)

In case you wish to force HTTPS for a particular folder you can use:
RewriteEngine On 
RewriteCond %{SERVER_PORT} 80 
RewriteCond %{REQUEST_URI} somefolder 
RewriteRule ^(.*)$ https://www.domain.com/somefolder/$1 [R,L]

---

