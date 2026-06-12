---
title: "Apache2 SSL Issues"
date: 2009-08-16
forum: General Help
---

### Post by own3mall on 2009-08-16
Why does SSL work when the ports.conf file is setup this way:

```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *
Listen 80

<IfModule mod_ssl.c>
# SSL name based virtual hosts are not yet supported, therefore no
# NameVirtualHost statement here
Listen 443

<VirtualHost *:443>
        ServerName 75.71.130.52
        DocumentRoot /var/www-ssl/
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined

SSLEngine on
SSLCertificateFile /etc/apache2/ssl/server.crt
SSLCertificateKeyFile /etc/apache2/ssl/server.key 

</VirtualHost>

</IfModule>



```

and not work when it is setup this way:

```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *
Listen 80

<VirtualHost *:80>
        ServerName 75.71.130.52:80
        DocumentRoot /var/www/
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

<IfModule mod_ssl.c>
# SSL name based virtual hosts are not yet supported, therefore no
# NameVirtualHost statement here
Listen 443

<VirtualHost *:443>
        ServerName 75.71.130.52
        DocumentRoot /var/www-ssl/
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined

SSLEngine on
SSLCertificateFile /etc/apache2/ssl/server.crt
SSLCertificateKeyFile /etc/apache2/ssl/server.key 

</VirtualHost>

</IfModule>



```

The above returns the following error:

```

ssl_error_rx_record_too_long

```

Can I not run both non-ssl virtual hosts and ssl virtual host together?

---

### Post by own3mall on 2009-08-29
Anyone?

---

