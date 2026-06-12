---
title: "Apache2 live web hosting problem NEED HELP!!!"
date: 2011-03-13
forum: General Help
---

### Post by shinsan on 2011-03-13
Hi there I'm new to this forum and to linux and I love it however I'm having small trouble with setting up my Apache2 web server to host my website.

the main problem I'm having right now is that when I browse to my website it keep going to the default Apache page and not my website pages.

here is my virtual host setup:

these are two separate file in the sites-available folder

THIS IS MY DEFAULT SETTINGS
```

<VirtualHost *:80>
        ServerAdmin email@email.com

        DocumentRoot /var/www/
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



```THIS IS MY WEBSITE VIRTUAL HOST SETTINGS

```


<VirtualHost mydomain.com:80>
        ServerAdmin email@email.com
        DirectoryIndex index.php index.html index.htm welcome.html
        DocumentRoot /var/www/mydomain.com/htdocs/
        ServerName www.mydomain.com
        ServerAlias mydomain.com
        ServerAlias *.mydomain.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/mydomain.com/htdocs/>
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






```First Question: 
Is my virtual host setup correctly or not?


Regarding my dns, Let me layout for you , basically I have my domain with yahoo.com with the DNS setup already done from yahoo as follows:

```
*.mydomain.com                   IN     A       **.***.***.** 
mail.mydomain.com        IN     A       **.***.***.** 
mydomain.com                        IN     A       **.***.***.** 
[www.mydomain.com]("http://www.mydomain.com/")        IN     A       **.***.***.** 
```ALL DONE FROM YAHOO.

I have no understanding on DNS setup and how it works so I'm a complete novice. 

SECOND question do i have to setup any sort of dns setting from my Linux server or has yahoo covered it for me already? 

Any help will be greatly appreciated 

thanks

---

### Post by shinsan on 2011-03-13
anybody

---

### Post by shinsan on 2011-03-13
OK I got it working now 

I had to enable the virtual host by using the command:

en2sites

---

