---
title: "forbidden????????!!!!!!!"
date: 2011-03-02
forum: General Help
---

### Post by vivek.pandey on 2011-03-02
hi everyone
  i installed apache2... but when i type localhost in my browser o get FORBIDDEN You don't have permission to access / on this server.
second thing when i go to filesystems/etc/ i cannot see apache2 folder neither can i find its log file in /var/log/apache2
but when i type vi /etc/apache2/apache2.conf i can see the configuration file
also typing /etc/apche2
gets me output that it is a directory and even i can change to this directory.
i tried all above things after logging as root  but same problem.. can anyone suggest me whats the solution 
thanx in advance to all

---

### Post by Mariane on 2011-03-02
"Forbidden" errors are often just a problem of file permissions. 

Mariane

---

### Post by vivek.pandey on 2011-03-02
> **Mariane said:**
> "Forbidden" errors are often just a problem of file permissions. 

Mariane

but i tried even loging in root and type localhost in my browser  but same error even with root

---

### Post by vivek.pandey on 2011-03-03
any replies please?

---

### Post by WorMzy on 2011-03-03
That error means that apache cannot read the contents of the folder.

```
sudo chmod +r /var/www
```

should fix that.

---

### Post by pqwoerituytrueiwoq on 2011-03-03
it is possible apache does not allow access from the computer you are browsing from 
check
/etc/apache2/sites-available/default
look for the deny part
i cant remember if it is set like that on ubuntu's apache or xampp for linux

---

### Post by vivek.pandey on 2011-03-03
> **WorMzy said:**
> That error means that apache cannot read the contents of the folder.

```
sudo chmod +r /var/www
```

should fix that.

thanx for your reply i tried your code but sorry to say nothing happened neither on terminal nor when i typed localhost in my browser..same error

---

### Post by vivek.pandey on 2011-03-03
> **pqwoerituytrueiwoq said:**
> it is possible apache does not allow access from the computer you are browsing from 
check
/etc/apache2/sites-available/default
look for the deny part
i cant remember if it is set like that on ubuntu's apache or xampp for linux

thanx for your reply
going through file systems i couldnt find /etc/apache2 it wasnt there..
but i tpyped on terminal and here is what i get
vivek@NEO:~$ sudo cat /etc/apache2/sites-available/default
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

n what do you mean by the deny part?

---

### Post by WorMzy on 2011-03-03
> **neo_aryan said:**
> thanx for your reply i tried your code but sorry to say nothing happened neither on terminal nor when i typed localhost in my browser..same error

Sorry, that probably should have been
```
sudo chmod +rx /var/www
```

if you still get a permission denied message after that, run

```
sudo chmod -R +r /var/www
```

Make sure that you don't make a mistake with that last command. A space in the wrong place could have disastrous results.

---

### Post by WorMzy on 2011-03-03
> **neo_aryan said:**
> <Directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
_allow from all_
</Directory>

This underlined line should be
```
_Allow from all_
```

But I don't know if the capitalisation will make any difference..

Make the change anyway, then restart the apache service:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by vivek.pandey on 2011-03-03
> **WorMzy said:**
> Sorry, that probably should have been
```
sudo chmod +rx /var/www
```

if you still get a permission denied message after that, run

```
sudo chmod -R +r /var/www
```

Make sure that you don't make a mistake with that last command. A space in the wrong place could have disastrous results.

thanx once again i copied-pasted your exact commands.. i didnt get anything on terminal and some forbidden error on localhost
:-(

---

### Post by CharlesA on 2011-03-03
Can you post the output of this in code tags please:

```
ls -l /var/www/
```

---

### Post by vivek.pandey on 2011-03-03
> **CharlesA said:**
> Can you post the output of this in code tags please:

```
ls -l /var/www/
```

thanx for your reply
here is the output

```
vivek@NEO:~$ ls -l /var/www/
total 4
lrwxrwxrwx 1 root root 48 Nov 13 14:20 cherokee-images -> /usr/share/cherokee/default-site/cherokee-images
lrwxrwxrwx 1 root root 43 Nov 13 14:20 index.html -> /usr/share/cherokee/default-site/index.html
-rw-r--r-- 1 root root 20 Mar  2 19:01 testphp.php
```

well cherokee here was the server i had installed earlier it was running ok but i later uninstalled it as i had to install lamp...and that test.php is a single line code phpinfo()
to check if php is working fine .. it was running fine

---

### Post by CharlesA on 2011-03-03
What are the permissions of the folders that those symlinks point to?

---

### Post by vivek.pandey on 2011-03-03
> **CharlesA said:**
> What are the permissions of the folders that those symlinks point to?

you talking about these?
/usr/share/cherokee/default-site/cherokee-images
/usr/share/cherokee/default-site/index.html

i uninstalled cherokee so they dont exist

---

### Post by WorMzy on 2011-03-03
Strange, I'd expect a 404 (file not found) then, rather than a 403 (access forbidden). Remove the links, then try again.

```
sudo rm /var/www/index.html /var/www/cherokee-images
```

---

### Post by vivek.pandey on 2011-03-03
> **WorMzy said:**
> Strange, I'd expect a 404 (file not found) then, rather than a 403 (access forbidden). Remove the links, then try again.

```
sudo rm /var/www/index.html /var/www/cherokee-images
```

thanx you are awesome 
its working now i have a white webpage which has index of/
name last modified size description and the file testphp.php

so i guess its working fine...will report any problems if i find but one question from where did you learn all those terminal command... i mean i too know many but they are not as high level as yours so please give me some advice

---

### Post by WorMzy on 2011-03-03
Well, mostly you pick them up from books, following online tutorials, or by reading posts on various forums. Nobody knows that many commands when they start out, but you pick them up as you go along if you look out for them.

The basics are fairly self explanatory: rm = remove, ls = list, cd = change directory, mkdir = make directory, man = manual

For less obvious commands, use the man command to find out more about them: man chmod, man chown, man chgrp, man grep, man sed.

Some commands aren't actually terminal commands at all, but are launchers for graphical applications, e.g.: gedit, firefox, gnome-appearance-properties, etc.. Some can still receive arguments from the command line though, e.g. gedit --new-document, firefox -P, etc..

Then of course you have daemon/service scripts, which are slightly different again. You have to call those with their full path, use the sudo (super user do) command with them*, and provide an action. e.g. sudo /etc/init.d/apache2 restart, sudo /etc/init.d/apache2 stop

Piping and redirects are a little harder to understand, since you can't use man to find information about them. This link should help you there though: [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)


*normally. Some daemon actions can be called without sudo, e.g. /etc/init.d/apache2 status

---

### Post by vivek.pandey on 2011-03-03
> **WorMzy said:**
> Well, mostly you pick them up from books, following online tutorials, or by reading posts on various forums. Nobody knows that many commands when they start out, but you pick them up as you go along if you look out for them.

The basics are fairly self explanatory: rm = remove, ls = list, cd = change directory, mkdir = make directory, man = manual

For less obvious commands, use the man command to find out more about them: man chmod, man chown, man chgrp, man grep, man sed.

Some commands aren't actually terminal commands at all, but are launchers for graphical applications, e.g.: gedit, firefox, gnome-appearance-properties, etc.. Some can still receive arguments from the command line though, e.g. gedit --new-document, firefox -P, etc..

Then of course you have daemon/service scripts, which are slightly different again. You have to call those with their full path, use the sudo (super user do) command with them*, and provide an action. e.g. sudo /etc/init.d/apache2 restart, sudo /etc/init.d/apache2 stop

Piping and redirects are a little harder to understand, since you can't use man to find information about them. This link should help you there though: [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)


*normally. Some daemon actions can be called without sudo, e.g. /etc/init.d/apache2 status

well thanks for your reply these commands are easy .. i was talking about these
sudo chmod +rx /var/www
sudo chmod -R +r /var/www

---

### Post by WorMzy on 2011-03-03
Read though man chmod, it'll explain what each of those commands do and more.

---

