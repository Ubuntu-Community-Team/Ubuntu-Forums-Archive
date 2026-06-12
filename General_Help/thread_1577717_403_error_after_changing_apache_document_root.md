---
title: "403 error after changing apache document root"
date: 2010-09-19
forum: General Help
---

### Post by batgranny on 2010-09-19
HI folks

I've had apache installed for a couple of years with no problem but this morning I thought I would change the apache document root to my secondary disk so that my WAMP setup in my Windows partition and LAMP could share the same files. 

I've edited the etc/apache2/sites-available file to point it to the new location of my document root but I am getting a 403 - forbidden "You don't have permission to access / on this server." error when I try to load files through the browser. 

I'm not sure if this is a permissions issue or the way I've edited the sites-available config, I was wondering if someone could help.  Here is the new sites available config:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /media/Data/webroot
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /media/Data/webroot>
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
```Any help you could give with this with this would be brilliant.

---

### Post by spjackson on 2010-09-21
The config looks OK to me, so I suspect that it is either file/directory ownership/permissions or you don't have an index.html (or equivalent).

/var/log/apache2/error.log should give you relevant information. Also, try accessing a url where you know that the file you specify does exist.

---

### Post by SeijiSensei on 2010-09-21
I usually get this error when I've pointed the DocumentRoot to a directory where the apache "user" has no rights.  The simplest solution is to make sure the entire website directory is world-readable by running the commands:

chmod go+rx /path/to/the/directoryroot
chmod go+r -R /path/to/the/directoryroot/*

The first command makes it possible to enter and list the directory.  The second command makes all the files in that directory (and any subdirectories via the -R switch) readable by any user.

Remember that the apache server processes run not as root, but as an ordinary user with limited permissions called "www-data" on Ubuntu.  The www-data user needs to be able to read all the files that make up your site.

---

### Post by batgranny on 2010-09-24
Bah, that didn't work.  I have a feeling it's something to do with the fact that the folder is on a different partition. I've had a look at the file permissions on the webroot folder and here are the results:  

drwx------ 1 user  user 16K 2010-09-22 23:30 bohill
drwx------ 1 user user   0 2010-09-22 21:33 form
-rw------- 2 user user  45 2010-09-19 13:49 index.html

As far as I know this means that the user only has permissions on this directory? I've tried to change the file permissions using sudo chmod 777 -R  /media/Data/webroot but that doesn't seemed to have had any effect.

---

### Post by WorMzy on 2010-09-24
It won't do. NTFS doesn't support UNIX file permissions, meaning that they have to be fake-set at mount time. Add an entry (or edit your existing one) to /etc/fstab for the NTFS partition, and add the following options:

```
utf8,uid=1000,gid=1000,umask=002
```

So the full entry may look something like this:

```
UUID=7A5C94995C94522D                     /media/Data        ntfs auto,users,utf8,uid=1000,gid=1000,umask=002 0 0
```

The uid=1000,gid=1000 sets the owner and group of the partition to the first user/group.
The umask=002 sets the file permissions for every file to 775 (-rwxrwxr-x), alter this as need be. Just remember that the value of umask is the inverse of what permissions you want.
The utf8 probably isn't necessary, but I use it anyway.
The UUID for your drive will be different. You can use /dev/sda1 or whatever if you prefer.

After you've added it to fstab, save the file and unmount the partition. You may need to create /media/Data with 'sudo mkdir /media/Data'.

Finally, run 'sudo mount -a' to mount everything in fstab to make sure it works.

---

### Post by Jan-A6VMX on 2011-07-23
@WorMzy: This did the trick! Don't forget to unmount the existing NTFS partition before you edit /etc/fstab and do the mount -a.

---

### Post by ZaHACKieL on 2012-03-26
Hi. I just installed LAMP server in my PC running Ubuntu 10.04. I followed the instructions from here : [https://help.ubuntu.com/community/ApacheMySQLPHP#To_install_the_default_LAMP_stack_in_Ubuntu_10.04_and_above](https://help.ubuntu.com/community/ApacheMySQLPHP#To_install_the_default_LAMP_stack_in_Ubuntu_10.04_and_above)

but after a virtual host pointing to a folder in my home, I get te 403 error:

Forbidden

You don't have permission to access /aim/ on this server.

I have all the permissions for that folder. Actually, I followed the same instructions for 3 Ubuntu 11.04 laptops and worked perfectly but I don't know why is not working here. My sites-available config file is :

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/aika/server/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/aika/server/>
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

I've tried lots of things but didn't make it work. Any help would be great, thanx!!

ZL

---

### Post by ZaHACKieL on 2012-03-27
Forget it, I fixed it by changing permissions of my home/user folder to 751 and my www folder to 711. I found the solution here :

[URL="http://ubuntuforums.org/showthread.php?t=1224005"]http://ubuntuforums.org/showthread.php?t=1224005
[/URL]
[http://ubuntuforums.org/showthread.php?t=1745500]("http://ubuntuforums.org/showthread.php?t=1745500")

---

### Post by Danxof on 2012-04-24
Amazing trick! Thanks! Also, to find the UUID of your units you can type in a terminal: blkid

Thanks!

---

### Post by natesymer on 2013-01-24
Simple fix for those with:

Error 403: You don't have permission to access "/" on this server

All you have to do is make sure that every directory in the path to your webroot is 755 (aka drwxr-xr-x).

Use namei to show you the permissions of every path component in your webfoot:

```
namei -m /path/to/webroot
```

then find any directory that isn't 755 and chmod it accordingly. 

Some directories that are automatically 755:
```

/
/media
/home
/home/<YOUR_USERNAME>
/var/www

```
(notice a pattern?)

---

