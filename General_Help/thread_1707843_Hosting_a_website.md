---
title: "Hosting a website?"
date: 2011-03-15
forum: General Help
---

### Post by UncleMonty on 2011-03-15
Is there anyway of hosting a website using ubuntu?

---

### Post by jcolyn on 2011-03-15
Download Ubuntu Server Edition at [http://www.ubuntu.com/business/get-ubuntu/download](http://www.ubuntu.com/business/get-ubuntu/download) and install it..

This is the easy part. Next the hardest. Purchase a domain name and then get a static IP and point the DNS to your IP.

However your internet provider may not like the additional bandwidth as a result..

---

### Post by ondemanddesign on 2011-03-15
> **UncleMonty said:**
> Is there anyway of hosting a website using ubuntu?

Using a LAMP environment (Linux (Ubuntu), Apache, mySQL, and PHP) you will have the basis of a web server. All you need to know is how to code in HTML/PHP. 

If you don't have LAMP installed you can do so through a visual text interface by using the command:

```
sudo tasksel
```

Within the menu that shows up simply select LAMP server (by using space) and apply the changes (by using enter)

example of output for tasksel
```
â    [*] LAMP server   â   â
```

If you are hosting this off of a standard ISP (Comcast, Qwest, ect.) then you will find that they block port 80. You can either redirect the port within your router if it supports it or run this command from the Ubuntu Server Terminal:

```
sudo vim /etc/apache2/ports.conf
```

The config file should look something like this:

```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

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

It should be as easy as changing the ports from 80 to something not blocked by your ISP. I use 8080. After that is done restart Apache

```
sudo service apache2 restart
```

This allows the configuration change to take effect.

---

### Post by Dutch70 on 2011-03-15
Nice tutorial to install LAMP...

[[COLOR="Blue"]http://www.howtogeek.com/howto/42480/how-to-turn-your-home-ubuntu-pc-into-a-lamp-web-server/[/COLOR]]("http://www.howtogeek.com/howto/42480/how-to-turn-your-home-ubuntu-pc-into-a-lamp-web-server/")

---

