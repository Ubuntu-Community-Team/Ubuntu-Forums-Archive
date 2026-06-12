---
title: "public_html not working"
date: 2010-10-23
forum: General Help
---

### Post by suresh_vandiyur on 2010-10-23
[http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/.i](http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/.i) used to configure the public_html in my system using the above link. but i did not get the phpinfo page if i run the it will ask download the phpinfo.php file. why this was asking and not showing the public_html files. what was the issue.

Thank you

---

### Post by efflandt on 2010-10-23
You shouldn't run links together with following text (".i") because that can break links.

Did you properly follow the instructions, including restarting apache after editing php5.conf that follows:

> Does your browser ask if you want to **download the php** file instead of displaying it? That&#8217;s because you may use Ubuntu 10.04 or later versions...Instructions following that works for me in Maverick.  If for some reason your browser cached the php file when it was not working, try clearing your browser cache or closing and restarting your browser.

However, even though phpmyadmin appeared to install properly, with Apache2 marked by default, it apparently did not make apache aware of itself.  So if you got php in general working above, but get 404 error after installing phpmyadmin, I had to do the following to get that to work:

```
sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/sites-enabled/.

sudo /etc/init.d/apache2 restart
```So now I just have to figure out what this would be useful for.  I did a lot of Perl cgi scripting (w/text databases) and some javascript years ago, but not SQL or php.

PS: It is probably best to make that a symlink instead in case phpmyadmin gets updated:

```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/sites-enabled/.

sudo /etc/init.d/apache2 restart
```

---

### Post by SeijiSensei on 2010-10-23
Copy the two files beginning with userdir in /etc/apache2/mods-available to /etc/apache2/mods-enabled.  Restart apache.

---

### Post by crichard on 2010-10-23
@suresh_vandiyur I request you to edit the URL, you mentioned, because it shows someother posts. you've to remove the .i which is at the end of the URL.   OK. Let's come to the topic. 

Please read that post carefully & follow the instructions, It has already mentioned  how to rectify this problem **Does your browser ask if you want to download the php file instead of displaying it?** 

You've to comment out few lines & restart the apache. Follow everything step by step, please don't skip any steps. Otherwise you may run into the problem. Happy LAMPing! :) I'm running LAMP server on both of my 10.04 & 10.10 machines without any problem. Hope I can hear the same from you. :)

---

### Post by suresh_vandiyur on 2010-11-03
> **crichard said:**
> @suresh_vandiyur I request you to edit the URL, you mentioned, because it shows someother posts. you've to remove the .i which is at the end of the URL.   OK. Let's come to the topic. 

Please read that post carefully & follow the instructions, It has already mentioned  how to rectify this problem **Does your browser ask if you want to download the php file instead of displaying it?** 

You've to comment out few lines & restart the apache. Follow everything step by step, please don't skip any steps. Otherwise you may run into the problem. Happy LAMPing! :) I'm running LAMP server on both of my 10.04 & 10.10 machines without any problem. Hope I can hear the same from you. :) your browser ask if you want to download the php file instead of displaying it?. yes still asking the browser ask the download a file.
Thank you

---

### Post by Muhammad El-Saeed on 2011-04-16
After installing userdir module

```
sudo gedit /etc/apache2/mods-enabled/php5.conf
```You'll see something like this
```
<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
    SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
    SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>
```Just comment this section to be like this

```
<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
    SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
    SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    #<IfModule mod_userdir.c>
    #    <Directory /home/*/public_html>
    #        php_admin_value engine Off
    #    </Directory>
    #</IfModule>
</IfModule>
```

then restart ur apache
```
sudo /etc/init.d/apache2 restart
```

---

