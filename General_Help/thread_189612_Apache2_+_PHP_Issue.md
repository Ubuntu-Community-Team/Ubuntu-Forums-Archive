---
title: "Apache2 + PHP Issue"
date: 2006-06-05
forum: General Help
---

### Post by noeluylee on 2006-06-05
I installed apache2 and php5 on my newly installed kubuntu 6.06. apache2 works fine, however php5 doesnt, when I test the php, it bring me a popup window, just like you're downloading something from the net. 

Before this, I am running Kubuntu 5.10 and I never had this problem.  after installing apache and php on my old system, without any configuration, its just works. 

please help.. thanks.

---

### Post by alanphil on 2006-06-05
Did you install Apache and PHP using Synaptic? If so, everything should be configured "out of the box".

If you installed using some other method, you may need to modify the Apache config file so it understands how to handle a .php page properly.

---

### Post by noeluylee on 2006-06-05
Hi, still not working.

I installed apache2 and php5 thru synaptics.

DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

and
I uncomment the follow:
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

it doesnt help! still not working. any more suggestions?

Thanks

---

### Post by alanphil on 2006-06-05
I would try stopping and restarting Apache. Then try a very simple PHP file, the common "phpinfo" example. I'm running the same setup on Ubuntu Dapper and it worked without any tweaking. Anything different in the Kubuntu version of these packages? :confused:

---

### Post by Meads on 2006-06-05
Use lighttpd it's much better and easier to configure than apache :)

---

### Post by noeluylee on 2006-06-05
yes, I did stop and start, but doesnt help either. yes, phpinfo() is the one im trying to open. 

any other suggestion?:rolleyes: :confused:

---

### Post by noeluylee on 2006-06-06
any help here? :( pleaseee... : :mrgreen:

---

### Post by thasheep on 2006-06-06
are your php files name something.php, something.phtml or something.php3?
The extension tells apache how to deal with the files. If you want to change the default to php, comment out the line 'DefaultType text/plain' in /etc/apache2/apache2.conf and replace it with```
DefaultType application/x-httpd-php
```Now anything that isn't a known type will be assumed to be php.

The known types are listed in /etc/mime.types, there should be the lines```
application/x-httpd-php                         phtml pht php
application/x-httpd-php-source                  phps
application/x-httpd-php3                        php3
application/x-httpd-php3-preprocessed           php3p
application/x-httpd-php4                        php4
```Add them if they're not there. On my computer, they're between the lines 'application/x-hdf....' and 'application/x-httpd-eruby....'

---

### Post by noeluylee on 2006-06-06
I did that, but still not working.

I checked ob /etc/mime.types, and I found these lines:
application/x-httpd-php                         phtml pht php
application/x-httpd-php-source             phps
application/x-httpd-php3                        php3
application/x-httpd-php3-preprocessed php3p
application/x-httpd-php4                        php4

I attached my apache2.conf (renamed to apache2conf.txt) for your reference,

Please tell me any other solutions for this problem.

Thanks.

---

### Post by thasheep on 2006-06-06
I just tried your apache2.conf and php works for me. I hadn't uncommented the 'AddType application/x-httpd-php(-source) .php(s)' lines but that made no difference. What does 'ls -l /etc/apache2/mods-enabled' produce? Mine does```
lrwxrwxrwx 1 root root 36 2006-04-20 18:48 cgi.load -> /etc/apache2/mods-available/cgi.load
lrwxrwxrwx 1 root root 37 2006-04-20 18:48 php5.conf -> /etc/apache2/mods-available/php5.conf
lrwxrwxrwx 1 root root 37 2006-04-20 18:48 php5.load -> /etc/apache2/mods-available/php5.load
lrwxrwxrwx 1 root root 40 2006-04-22 00:29 userdir.conf -> /etc/apache2/mods-available/userdir.conf
lrwxrwxrwx 1 root root 40 2006-04-22 00:29 userdir.load -> /etc/apache2/mods-available/userdir.load
```And all the links are blue (which means the files they point to exist).

---

### Post by ifokkema on 2006-06-06
[QUOTE=noeluylee]any help here? :( pleaseee... : :mrgreen:[/QUOTE]

Hi,

Did you run
```
sudo a2enmod php5
```
then restart apache, and try again.

Ivo

---

### Post by noeluylee on 2006-06-06
Mine is... after "sudo a2enmod php5"

```
lrwxrwxrwx 1 root root 36 2006-06-05 20:43 cgi.load -> /etc/apache2/mods-available/cgi.load
lrwxrwxrwx 1 root root 37 2006-06-06 20:01 php5.conf -> /etc/apache2/mods-available/php5.conf
lrwxrwxrwx 1 root root 37 2006-06-06 20:01 php5.load -> /etc/apache2/mods-available/php5.load
lrwxrwxrwx 1 root root 40 2006-06-04 01:36 userdir.conf -> /etc/apache2/mods-available/userdir.conf
lrwxrwxrwx 1 root root 40 2006-06-04 01:36 userdir.load -> /etc/apache2/mods-available/userdir.load

```


hmmm, still doesnt work... :(

---

### Post by ifokkema on 2006-06-06
[QUOTE=noeluylee]Mine is... after "sudo a2enmod php5"

```
lrwxrwxrwx 1 root root 36 2006-06-05 20:43 cgi.load -> /etc/apache2/mods-available/cgi.load
lrwxrwxrwx 1 root root 37 2006-06-06 20:01 php5.conf -> /etc/apache2/mods-available/php5.conf
lrwxrwxrwx 1 root root 37 2006-06-06 20:01 php5.load -> /etc/apache2/mods-available/php5.load
lrwxrwxrwx 1 root root 40 2006-06-04 01:36 userdir.conf -> /etc/apache2/mods-available/userdir.conf
lrwxrwxrwx 1 root root 40 2006-06-04 01:36 userdir.load -> /etc/apache2/mods-available/userdir.load

```


hmmm, still doesnt work... :([/QUOTE]


To be sure, could you confirm:
- You restarted apache
- You tested your phpinfo() test file again, and was offered a download
- The downloaded file contains your PHP code (thus NO PHP processing)

---

### Post by noeluylee on 2006-06-06
Thanks guys, it worked after I re-install apache2 and php5. :)

---

