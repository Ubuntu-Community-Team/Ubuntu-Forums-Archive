---
title: "Can't access my website from the internet"
date: 2011-11-28
forum: General Help
---

### Post by scottyf11 on 2011-11-28
Hello all!

I've setup apache2 before but for some reason I cannot figure it out this time.  It works on my local network but I cannot access it from outside the local network.  I've been playing with it for hours and I feel like I'm getting no where.  The website is [www.competitivevantage.com](www.competitivevantage.com) and here are my files

End of /etc/apache2/apache2.conf
```
# Include the virtual host configurations:
Include sites-enabled/

ServerName competitivevantage.com

```

/etc/apache2/httpd.conf
```

ServerName competitivevantage.com 

```

/var/apache2/ports.conf
```

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

/etc/apache2/sites-available/competitivevantage.com
```



NameVirtualHost *:80

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
        ServerName competitivevantage.com
 
	DocumentRoot /var/www/web
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>



	<Directory /var/www/web>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>


ErrorLog /var/log/apache2/error.log







	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On


    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

/etc/hosts
```


127.0.0.1	localhost localhost.localdomain my-pc 


127.0.1.1	my-pc 
192.168.0.100  competitivevantage.com
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

end of /var/log/apache2/access.log
```

127.0.0.1 - - [28/Nov/2011:16:36:45 -0500] "GET /images/cstrip.gif HTTP/1.1" 200 658 "http://localhost/style.css" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
127.0.0.1 - - [28/Nov/2011:16:36:45 -0500] "GET /images/pic.jpg HTTP/1.1" 200 61709 "http://localhost/style.css" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
127.0.0.1 - - [28/Nov/2011:16:36:45 -0500] "GET /images/fstrip1.gif HTTP/1.1" 200 557 "http://localhost/style.css" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.0.100 - - [28/Nov/2011:17:45:55 -0500] "GET / HTTP/1.1" 200 1187 "-" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.0.100 - - [28/Nov/2011:17:45:55 -0500] "GET /style.css HTTP/1.1" 200 1387 "http://192.168.0.100/" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.0.100 - - [28/Nov/2011:17:45:55 -0500] "GET /images/cstrip.gif HTTP/1.1" 200 658 "http://192.168.0.100/style.css" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.0.100 - - [28/Nov/2011:17:45:55 -0500] "GET /images/pic.jpg HTTP/1.1" 200 61709 "http://192.168.0.100/style.css" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.0.100 - - [28/Nov/2011:17:45:55 -0500] "GET /images/fstrip1.gif HTTP/1.1" 200 556 "http://192.168.0.100/style.css" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.0.100 - - [28/Nov/2011:17:45:55 -0500] "GET /favicon.ico HTTP/1.1" 404 502 "-" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.0.100 - - [28/Nov/2011:17:45:55 -0500] "GET /favicon.ico HTTP/1.1" 404 502 "-" "Mozilla/5.0 (X11; Linux i686; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"

```

end of /var/log/apache2/error.log
```

[Mon Nov 28 17:43:58 2011] [notice] SIGUSR1 received.  Doing graceful restart
[Mon Nov 28 17:43:58 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
[Mon Nov 28 17:43:58 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 17:45:55 2011] [error] [client 192.168.0.100] File does not exist: /var/www/favicon.ico
[Mon Nov 28 17:45:55 2011] [error] [client 192.168.0.100] File does not exist: /var/www/favicon.ico
[Mon Nov 28 17:50:36 2011] [notice] SIGUSR1 received.  Doing graceful restart
[Mon Nov 28 17:50:36 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
[Mon Nov 28 17:50:36 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 17:52:44 2011] [notice] SIGUSR1 received.  Doing graceful restart
[Mon Nov 28 17:52:44 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:09:15 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:09:16 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:10:29 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:10:29 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:14:19 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:14:20 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:14:37 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:14:37 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:17:08 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:17:09 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:18:05 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:18:06 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:34:27 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:34:28 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:35:16 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:35:17 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations
[Mon Nov 28 18:35:47 2011] [notice] caught SIGTERM, shutting down
[Mon Nov 28 18:35:48 2011] [notice] Apache/2.2.20 (Ubuntu) configured -- resuming normal operations

```

I think this is every file that I've touched...

Thank you for any help!

---

### Post by homemadejam on 2011-11-28
I've just tried the link you gave, and I can access it no problem.

---

### Post by haqking on 2011-11-28
Is it public facing or behind a router ?

If it is behind a router then your WAN IP needs to be set to port forward to your server LAN IP.

Also if your WAN IP is dynamic then the you need to use dynamic DNS or or get a static IP.

Cheers

Edit: yeah works for me too, so problem with your device or location.

If you are trying to access it remotely from within your LAN then that often does not work for loopback, but if you are outside your LAN then it should work, probably the device or connection you are using to check it.

---

### Post by scottyf11 on 2011-11-28
hmm weird.  any idea why I can't access it locally?  I never had this problem before.

Thanks though I'm glad its working!  Time to put the temp page back up

---

### Post by efflandt on 2011-11-28
Most broadband routers (and Linux by default) do NOT do loopback [LAN2LAN via WAN (public) IP].  That is probably because a LAN IP coming in the public interface could be some sort of spoof attack. So you need to test your website from somewhere else on the internet, or through dialup or mobile data device not on your LAN.

If you are using Linux as your internet router something could likely be done with iptables to get around that.  But a true test is to test it from the internet (to make sure that your ISP is not blocking web access to you, which is common for cable companies).

---

### Post by haqking on 2011-11-28
> **scottyf11 said:**
> hmm weird.  any idea why I can't access it locally?  I never had this problem before.

Thanks though I'm glad its working!  Time to put the temp page back up

yes as i said in my edit and the post above this one, most home routers do not loopback.  test it on a smartphone or something, but as we said we can see it so it works.

To access it locally use your local address, to access remotely from local then you could use a proxy such as hidemyass.com or similar

---

### Post by scottyf11 on 2011-11-29
Ok thank you all very much!!!

---

