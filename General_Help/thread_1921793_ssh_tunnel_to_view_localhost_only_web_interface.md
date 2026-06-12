---
title: "ssh tunnel to view localhost only web interface"
date: 2012-02-07
forum: General Help
---

### Post by Mia_tech on 2012-02-07
guys, is it possible to use ssh tunnel to redirect my browser to access remote web interface, which is accessible only by localhost.

Thanks

---

### Post by pqwoerituytrueiwoq on 2012-02-07
can't you set up some port forwarding?
even if port 80 is in use or disabled by your isp you can still use any of the 60 some thousand ports and have it point to port 80 on the local network
if yuor issue is needing a login it is fairly eay to solve
i set a login on for mine that is only external by setting 2 ports for the same web content i set a login in the server config for that port
port 82 has a login while port 80 does not port 80 is only accessible via local net but port 82 is accessible remotely
```
~$ cat /etc/apache2/sites-available/scanner 
ServerName my-room
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /home/www-data/scanner
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/www-data/scanner/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    ErrorLog /var/log/apache2/error.log
    CustomLog /var/log/apache2/access.log combined
</VirtualHost>
<VirtualHost *:82>
    ServerAdmin webmaster@localhost
    DocumentRoot /home/www-data/scanner
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/www-data/scanner/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
        AuthName "Please Login"
        AuthType Basic
        AuthUserFile /etc/apache2/users
        AuthGroupFile /dev/null
        require valid-user
    </Directory>
    ErrorLog /var/log/apache2/error.log
    CustomLog /var/log/apache2/access.log combined
</VirtualHost>
~$ cat /etc/apache2/ports.conf 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80
NameVirtualHost *:81
Listen 81
NameVirtualHost *:82
Listen 82
NameVirtualHost *:83
Listen 83

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
~$ cat /etc/apache2/users
LoginName:MD5_sum_of_pasword
```

---

### Post by Khayyam on 2012-02-07
Mia_tech ...

Its been a while since I needed to do this but the following should work as advertised.

```
ssh -L 8080:localhost:80 <remote_ip or domain name>
```

You would then direct your browser to localhost:8080

HTH ...

---

### Post by HermanAB on 2012-02-07
Depending on your exact problem, you can also use a SSH socks proxy.

---

### Post by Mia_tech on 2012-02-08
I've been testing it with Khayyam solution, but I've tried configuring my browser and without configuring the browser (failed)... what would be the socks proxy solution. By the way the connections is ssl encrypted [https://localhost:8080](https://localhost:8080)

Thanks

---

### Post by Khayyam on 2012-02-08
Mia_tech ..

If the port you are forwarding is 443 (ssl) and not 80 (www) you need to assign that port

```
ssh -L 8080:localhost:443 <remote_ip or domain name>
```This will be transparent to the browser as 443 is forwareded to localhost:8080

best ...

---

### Post by Mia_tech on 2012-02-08
> **Khayyam said:**
> Mia_tech ..

If the port you are forwarding is 433 (ssl) and not 80 (www) you need to assign that port

```
ssh -L 8080:localhost:433 <remote_ip or domain name>
```

This will be transparent to the browser as 443 is forwareded to localhost:8080

best ...

I'm not sure if your command will work because when working with the browser you know what port you will be connecting to, but you don't know what it's the local port. Browsers open a bunch of different ports when accessing the web servers.... so I think it has to be socks proxy

---

### Post by Mia_tech on 2012-02-08
actually... it did work!

Thanks

---

### Post by Khayyam on 2012-02-08
> **Mia_tech said:**
> actually... it did work! Thanks

Mia_tech ..

Your welcome .. I'd made a typo, port '433' instead of '443' (corrected) .. and so I was just about to reply when I saw you had.

Please [mark this thread as [SOLVED]]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6")

best ...

---

