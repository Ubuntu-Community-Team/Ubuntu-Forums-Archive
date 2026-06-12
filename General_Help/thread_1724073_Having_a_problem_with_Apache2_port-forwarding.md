---
title: "Having a problem with Apache2 port-forwarding"
date: 2011-04-07
forum: General Help
---

### Post by espressobeanie on 2011-04-07
Hi. I'm having problems with some simple port forwarding in Apache2. My issue is that I have told Apache to listen on Ports 80 and 4400. When I web-browser in [http://localhost:80](http://localhost:80), I can see the site. When I web-browse in [http://localhost:4400](http://localhost:4400), I only get an Apache 404 - Not found reply. Below is my ports.conf file. Does anyone know what I'm doing wrong?

ports.conf:
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80
Listen 4400

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```

---

### Post by pqwoerituytrueiwoq on 2011-04-07
is there a virtual host running on that port
/etc/apache2/sites-available/default
```
        <VirtualHost *:4400>
            DocumentRoot /foo/bar # /foo/bar could be /var/www or /home/bob/public_html for example
            <Directory /foo/bar>
                Options FollowSymLinks # follows symbolic links
                AllowOverride All # allows use of .htaccess
                Order allow,deny #allows everyone to access it via browser
                allow from all
            </Directory>
        </VirtualHost>>
```
you may also need *NameVirtualHost *:4400* in ports.conf

---

### Post by espressobeanie on 2011-04-07
There isn't. There's only the default port 80 and my httpd.conf file only contains the line: "DirectoryIndex index.html". I did get the site working as I wanted. I don't have a .htaccess file in the index directory

I don't understand the need for a NameVirtualHost. Is there any documentation floating on the web that describes the necessity when port forwarding a website?

---

