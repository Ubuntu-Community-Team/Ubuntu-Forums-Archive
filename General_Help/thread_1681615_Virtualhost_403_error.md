---
title: "Virtualhost 403 error"
date: 2011-02-04
forum: General Help
---

### Post by geodanny on 2011-02-04
I am setting up a virtualhost to run a local dev instance of drupal on my laptop. But I keep running into a 403 error: "Forbidden    You don't have permission to access /index.html on this server.   Apache/2.2.16 (Ubuntu) Server at drupal-7 Port 80"

Is there anything you would suggest I try to resolve the error? Any additional info you need? I looked through a number of threads and none of the solutions on those appear to correct my problem.

I followed instructions I found at: 
[http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/](http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/)
[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

Essentially, I copied the default config file and then modified it slightly to fit with the instructions on those pages. I get no errors when restarting apache.

I also made the www-data user is a user of my user group 'danny'
```
sudo usermod -g danny www-data
```

I updated the permissions for the files. My files are located in my home directory: /home/danny/workspace/drupal-7/. I set permissions recursively on the workspace directory
```
sudo chmod -R 775 workspace
```

drwxrwxr-x  3 danny danny  4096 2011-02-04 08:17 workspace
....
drwxrwxr-x 9 danny danny 4096 2011-02-04 08:39 drupal-7
-rwxrwxr-x 1 danny danny   41 2011-02-04 08:17 index.html

The URL I am attempting to use is: [http://drupal-7/](http://drupal-7/)


/etc/apache2/sites-available/drupal-7
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName drupal-7

	DocumentRoot /home/danny/workspace/drupal-7/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/workspace/drupal-7/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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

```

tail -f /var/log/apache2/error.log 
```
[Fri Feb 04 08:39:54 2011] [notice] caught SIGTERM, shutting down
[Fri Feb 04 08:39:55 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Fri Feb 04 08:39:58 2011] [error] [client 127.0.0.1] (13)Permission denied: access to / denied
[Fri Feb 04 08:57:11 2011] [error] [client 127.0.0.1] (13)Permission denied: access to /index.php denied
[Fri Feb 04 09:57:09 2011] [error] [client 127.0.0.1] (13)Permission denied: access to /index.html denied

```

/etc/hosts/
```
192.168.1.65	dell-pickle	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	dell-pickle	localhost6.localdomain6	localhost6

# Localhost and virtualhosts
127.0.0.1      localhost	drupal-7
127.0.1.1	dell-pickle

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

BTW: [http://localhost/](http://localhost/) gives the "It works!" default page.

---

### Post by geodanny on 2011-02-05
I think, but am not sure, that I found the cause of my problem. My home folder is encrypted with encryptfs. I did not realize I had encrypted it, likely as part of the 10.10 install process.

Can someone confirm that encryptfs would cause just such a 403 forbidden error? I assume it would since the user www-data would not necessarily have the correct key to unlock my encrypted data. That is, unless I were to supply www-data with my key, which is not something I would want to do. I did some searches but did not find anything that actually confirms my suspicions. 

If encryptfs is the reason for the 403 errors, do you know if there is a reasonably easy way to encrypt only part of my home folder (documents, .evolution, etc) but not the entire thing?

I did find some support for my guess. I logged in as www-data. There are two users with home folders in /home/ I could not log into mine (encrypted) but I could log into the other user's home folder (not encrypted).


```

sudo su www-data 
[sudo] password for danny: 
$ cd /home/danny/
cd: 1: can't cd to /home/danny/
$ cd /home/        
$ ls
brett  danny  lost+found
$ cd brett 
$ ls
Templates          Desktop          Videos
Documents          Downloads        Pictures
Public

```

In the meantime, I have a workaround operational. I moved my workspace folder to /home/workspace/ That way my dev workspace is located on the partition with my /home/ folder.

If encryptfs is the problem and there is no easy way to encrypt only part of my home folder, I'll probably leave it as is despite not being completely ideal.

---

