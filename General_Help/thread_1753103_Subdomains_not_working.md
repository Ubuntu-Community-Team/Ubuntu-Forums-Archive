---
title: "Subdomains not working"
date: 2011-05-08
forum: General Help
---

### Post by galileo005 on 2011-05-08
Ubuntu 10.04, apache 2.214, webmin 1.540
Yesterday when i was working on my home server and added a new vhost via webmin everything worked fine. Ill call it subdomain.name
Today I added another vhost subdomain2.name and now the subdomains of name are not able to be found by my browsers. I didn't check before I added the new vhost whether the subdomains I had already got were working when I booted up.

name still works when I type in [http://name](http://name)
but [http://subdomain(s).name]("http://subdomain%28s%29.name") do not.

I created the virtual server in webmin, called subdomain2.name and pointed to 192.168.1.64 like before and added it to the etc/hosts file (as well as the hosts file in windows) and then checked the sites-enabled folder - all fine. Applied changes and restarted apache on the command line.
I'm not getting any errors in/var/log/apache2/error.log

000-default:
 NameVirtualHost *:80
<VirtualHost *:80>
      ServerAdmin webmaster@localhost
      ServerName websites2
DocumentRoot /var/www
      <Directory />
            Options FollowSymLinks
            AllowOverride None
      </Directory>
      <Directory /var/www/>
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

  
subdomain.name.conf:
 <VirtualHost 192.168.1.64:80>
ServerName subdomain.name
DocumentRoot /home/name/public_html/subdomain/html
<Directory  /home/name/public_html/subdomain/html>
allow from all
Options +Indexes
</Directory>
</VirtualHost>


Hosts:
127.0.0.1 localhost
192.168.1.64 websites2
192.168.1.64 name
192.168.1.64 subdomain.name

I've also stopped and stared apache from webmin but no change.
Why would it work one day and not the next?

---

### Post by satanselbow on 2011-05-08
Is your 192.168... address static? ie manually entered in connection settings and is persistent between reboots?

---

### Post by galileo005 on 2011-05-08
> **satanselbow said:**
> Is your 192.168... address static? ie manually entered in connection settings and is persistent between reboots?
Yes, static ethernet ip address in my home network

---

### Post by galileo005 on 2011-05-10
Anyone?

---

### Post by galileo005 on 2011-05-12
Solved!
For some reason when I changed my c:/windows/system32/drivers/etc/hosts file
on my Administrator account, as it wouldn't let me on my default account, it deleted my default hosts file.

I didn't think there was two(unless it was hidden somehow), as it was still on my admin account which was the only one I was checking.

So I made a new one and works fine. Bloody windows!

---

