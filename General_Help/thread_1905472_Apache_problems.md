---
title: "Apache problems"
date: 2012-01-06
forum: General Help
---

### Post by ialvik on 2012-01-06
Hi 

Im trying to et up subdomains in apache so the urls would be like:

 nzb.xxxxxxx.com
movies.xxxxxx.com

but I still have to write the portnumber too..

This is my sites-available/default file

> <VirtualHost *:80>
        ProxyPass  / [http://localhost:8080](http://localhost:8080)
        ProxyPassReverse / [http://localhost:8080](http://localhost:8080)
        ServerName nzb.xxxxxxx.com
        Order allow,deny
        allow from all
        </VirtualHost>

<VirtualHost *:80>
        ProxyPass  / [http://localhost:8081](http://localhost:8081)
        ProxyPassReverse / [http://localhost:8081](http://localhost:8081)
        ServerName tv.xxxxxx.com
        Order allow,deny
        allow from all
        </VirtualHost>

<VirtualHost *:80>
        ProxyPass  / [http://localhost:8083](http://localhost:8083)
        ProxyPassReverse / [http://localhost:8083](http://localhost:8083)
        ServerName film.xxxxxxx.com
        Order allow,deny
        allow from all
        </VirtualHost>



The apache2.conf file is  empty, and how do I setup httpd.conf?

sorry the apache2.conf isn't empty

>  Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /www/var
ServerName xxxxxxx.com

# Other directives here

</VirtualHost>

#<VirtualHost *:80>
#DocumentRoot /www/example2
#ServerName [www.example2.org](www.example2.org)

# Other directives here

#</VirtualHost>

---

### Post by ialvik on 2012-01-06
Error message

> ver@m58p:/etc/apache2$ sudo service apache2 restart
 * Restarting web server apache2                                                                                        Warning: DocumentRoot [/www/var] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Warning: DocumentRoot [/www/var] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/error_log.
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                                                                 [fail]


A bit unsure of what i should use as DocumentRoot here

---

### Post by lisati on 2012-01-06
> **ialvik said:**
> Error message



A bit unsure of what i should use as DocumentRoot here

"DocumentRoot" usually identifies the folder where you will place the files and folders your website will use.

---

### Post by topsites on 2012-01-06
Google httpd.conf

---

### Post by ialvik on 2012-01-06
I'm know, but I dont know where they are for programs like sabnzbd, couchpotato an sickbeard?

---

### Post by lisati on 2012-01-06
> **ialvik said:**
> I'm know, but I dont know where they are for programs like sabnzbd, couchpotato an sickbeard?

Have you actually installed those programs?

---

### Post by ialvik on 2012-01-07
Their installed and working, but the domains are not working right..

I guess should not point DocumentRoot to /etc/default... 

The problem is they put files in so many directorys so i really dont know the which one that is DocumentRoot

---

### Post by topsites on 2012-01-07
This is not any of my business, how you are using Ubuntu and what for, but if per chance you are attempting to run a Web site from your home PC it would be far easier to simply rent an already set-up virtual domain server that will host your web site because I can tell you this is only the beginning of your headaches.

Seriously man, you're dealing with server administration that Unix die hard fanatics cringe at, the httpd conf file is no fun for even the experts, plus I think it's a little beyond the scope of this forum's support ... You know, the people in this forum are just folks like you and I and I've even leased my own dedicated server before but it's been some years and I think you're asking a bit much, if this httpd conf is over your head, it would be easier to just spend the $4 a month or so ...

I think...

Now if that's not the case we can try and hack at it a bit longer but...

---

### Post by ialvik on 2012-01-07
I had it working before.. it wasn't that hard to set it up.. but have a new server and can't just find the right side on Google.. But I'm gonna open a bootle of wine and sit down and try som more :)

Since there iis sabnzbd and sickbird i cant rent a web hotel..

---

### Post by ialvik on 2012-01-07
Maybe i'm missing som proxy modules?

---

