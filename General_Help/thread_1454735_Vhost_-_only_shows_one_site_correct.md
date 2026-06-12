---
title: "Vhost - only shows one site correct"
date: 2010-04-15
forum: General Help
---

### Post by Myx0.x3 on 2010-04-15
Hi!

I got my VPS last day and i deside to setup everything myself, but i just came to virtualhost in apache when i got stuck.

**i have Ubuntu Server 9.10 whit Apache2**

Let me begin to show my config files.

ports.conf
```

#NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>


```

in sites-available i have my two domain whit the vhost config..

in my first:
[www.kirbynet.se](www.kirbynet.se) (its the name of the file)
```

#NameVirtualHost *
<VirtualHost *>
        ServerName  kirbynet.se
        ServerAlias *.kirbynet.se
        DocumentRoot /var/www/kirbynet/httpdocs
        # Logfiles
        #ErrorLog  /var/www/kirbynet/logs/error.log
        #CustomLog /var/www/kirbynet/logs/access.log combined
</VirtualHost>


```

[www.grobladet.com](www.grobladet.com) (my other name of the file)
```

#NameVirtualHost *
<VirtualHost *>
        ServerName  grobladet.com
        ServerAlias *.grobladet.com
        DocumentRoot /var/www/grobladet/httpdocs

        # Logfiles
        #ErrorLog  /var/www/grobladet/logs/error.log
        #CustomLog /var/www/grobladet/logs/access.log combined
</VirtualHost>

```

i have also changed in my /var/www/index.html in the last row (dont ask me why :P)


```

/etc/apache2/sites-enabled# ls -l
total 0
lrwxrwxrwx 1 root root 26 Jan 22 11:21 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root 36 Apr 14 18:48 www.grobladet.com -> ../sites-available/www.grobladet.com
lrwxrwxrwx 1 root root 34 Apr 14 18:48 www.kirbynet.se -> ../sites-available/www.kirbynet.se


```

But when i go to [http://kirbynet.se](http://kirbynet.se) the vhost works, but when i enter [http://grobladet.com](http://grobladet.com) it does not work! it only shows me a index.html witch is not my own i made, this is the wierd part..

please help me get this thing to work!

i hope i provided you all the information you guys need!

---

### Post by steev182 on 2010-04-15
I guess that you've already restarted apache?

I'm gonna try this on my computer to see if I can replicate. I remember setting up vhosts before, having similar problems to this and finding it was a simple fix in the end.

Really wish I'd blogged/wiki'd it!

---

### Post by Myx0.x3 on 2010-04-15
> **steev182 said:**
> I guess that you've already restarted apache?

I'm gonna try this on my computer to see if I can replicate. I remember setting up vhosts before, having similar problems to this and finding it was a simple fix in the end.

Really wish I'd blogged/wiki'd it!

Yes i have restarted or reloaded (most times reloaded) it after i changed in a config file.

hehe, i have read like 3-4 different "tutorials" but all are different, so i dont know witch one that works..

---

