---
title: "Apache Problem when changing website root? plz"
date: 2011-09-06
forum: General Help
---

### Post by g{Lv$qjC8w2 on 2011-09-06
Hey
I want to change the site root but httpd.conf was emty ;/ so i found inside  /sites-available there was a default document which was where i change the site root, from /var/www  to /home/desktop/www

(desktop is my user)

Anyway when i restarted the apache service, i now get this error :@

(13) Permission Denied: make_sock: could not bind to address 0.0.0.0:80 no listening sockets available, shutting down

Unable to open logs.

Heres the config, any ideas? It WAS WORKING FINE before i changed it

```

ServerAdmin webmaster@localhost

    DocumentRoot /home/desktop/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www>
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

```

-

THANK YOU IN ADVANCE
George :confused:

---

### Post by Bobhuber on 2011-09-06
> **cartoongeorge96 said:**
> Hey
I want to change the site root but httpd.conf was emty ;/ so i found inside  /sites-available there was a default document which was where i change the site root, from /var/www  to /home/desktop/www

(desktop is my user)

Anyway when i restarted the apache service, i now get this error :@

(13) Permission Denied: make_sock: could not bind to address 0.0.0.0:80 no listening sockets available, shutting down

Unable to open logs.

Heres the config, any ideas? It WAS WORKING FINE before i changed it

```

ServerAdmin webmaster@localhost

    DocumentRoot /home/desktop/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www>
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

```-

THANK YOU IN ADVANCE
George :confused:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by g{Lv$qjC8w2 on 2011-09-07
> **Bobhuber said:**
> [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Thanks, but no thanks. Didn't really help me because i don't understand much with linux, nor does anything in that document refer to my problem.

Thanks, So frustrating :(

---

### Post by Bobhuber on 2011-09-07
> **cartoongeorge96 said:**
> Thanks, but no thanks. Didn't really help me because i don't understand much with linux, nor does anything in that document refer to my problem.

Thanks, So frustrating :(
It pertains DIRECTLY to your problem if you had read the entire post.


[LIST]****
[*]**[B]Change the DocumentRoot to point to the new location. For example, /home/user/public_html/ **[/B]
[*]**[B]Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>**[/B]
****
[/LIST]

---

### Post by g{Lv$qjC8w2 on 2011-09-07
> **Bobhuber said:**
> It pertains DIRECTLY to your problem if you had read the entire post.


[LIST]
[*]**[B]Change the DocumentRoot to point to the new location. For example, /home/user/public_html/ **[/B]
[*]**[B]Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>**[/B]
[/LIST]

  Apologies for missing this, Perhaps you missed something in my first post, this is what i did, successfully. I doubled checked and added the / on the end of the folders, still getting the same problem. I appreciate your help very much, i may have made a mistake, although i'm sure i didn't. I attached a screenshot of what im trying to do in terminal.

Many thanks and good returns

[IMG]http://i55.tinypic.com/2zdvln4.png[/IMG]

---

### Post by WorMzy on 2011-09-07
You're not running the start command as root. Try

```
sudo /etc/init.d/apache2 start
```

---

### Post by g{Lv$qjC8w2 on 2011-09-07
> **WorMzy said:**
> You're not running the start command as root. Try

```
sudo /etc/init.d/apache2 start
```
I actually cannot believe it..... YOU BEAUTY!!!!!!!! It WORKS!!

Thank you soo very much, stupid superuser :L

---

