---
title: "Apache2 Tomcat6 Virtual Hosts"
date: 2010-06-01
forum: General Help
---

### Post by unix_user on 2010-06-01
I am checking into issue with Apache2-Tomcat6 setup where second virtual site isn't
displaying the page correctly. There may be a misconfiguration in setup and can
someone point me where the issue could be.

Environment: Ubuntu 10.4, Tomcat6, Apache2 Name based virtual hosting
System is setup with ddclient to update ip address periodically.

There are 2 domains registered with dyndns - first site responds with content set in its DocumentRoot and 
second site displays index.html of Tomcat (/var/lib/tomcat6/webapps/ROOT/index.html) instead of what is setup in its
DocumentRoot (/home/user/k/webapps/ROOT/)


/etc/apache2/apache2.conf
    # Include all the user configurations:
    Include /etc/apache2/httpd.conf

    # Include ports listing
    Include /etc/apache2/ports.conf

    # Include the virtual host configurations:
    Include /etc/apache2/sites-enabled/


/etc/apache2/ports.conf
NameVirtualHost *:80
Listen 80

/etc/apache2/sites-available/a.dyndns.org
    <VirtualHost *:80>
        ServerName a.dyndns.org
        ServerAlias [http://a.dyndns.org](http://a.dyndns.org)
        ServerAdmin xxxx
        DocumentRoot /home/user/a/webapps/ROOT/

        <Directory />
                        Options FollowSymLinks
                        AllowOverride None
        </Directory>
        <Directory /home/user/a/webapps/ROOT/>
                        Options Indexes FollowSymLinks MultiViews
                        AllowOverride None
                        Order allow,deny
                        allow from all
        </Directory>
    </VirtualHost>


/etc/apache2/sites-available/k.dyndns.org
<VirtualHost *:80>
        ServerName k.dyndns.org
        ServerAlias [http://k.dyndns.org](http://k.dyndns.org)
        ServerAdmin webmaster@localhost
        JkMount / worker1
        JkMount /* worker1
        DocumentRoot /home/user/k/webapps/ROOT/

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/user/k/webapps/ROOT/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
    
</VirtualHost>

Testing:
$ wget a.dyndns.org -O -    # prints contents in DocumentRoot
wget k.dyndns.org -O -        # prints index.html in /var/lib/tomcat6/webapps/ROOT/index.html)

$ apache2ctl -t -D DUMP_VHOSTS
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         default server a.dyndns.org (/etc/apache2/sites-enabled/a.dyndns.org:1)
         port 80 namevhost a.dyndns.org (/etc/apache2/sites-enabled/a.dyndns.org:1)
         port 80 namevhost k.dyndns.org (/etc/apache2/sites-enabled/k.dyndns.org:1)
Syntax OK

---

