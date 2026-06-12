---
title: "folder Permission setting"
date: 2011-02-05
forum: General Help
---

### Post by spindler on 2011-02-05
I am having problems with my permission setting in my home directory.  I am using Ubuntu as a webserver and I have a number of wordpress websites. 

The user I log into the system is "USER"
The home folder is titled "USER"
Inside the USER folder I have a folder titled "WEBSITE"
Inside the WEBSITE folder I have a wordpress website.

I have set up VFTP  so I can update my wordpress files using FTP.  I am using the USER name and password to do this.  I am able to log into my website from another computer and update the files using the ftp services within wordpress in order to update the version of wordpress and the plug-ins.

The problem I am having is that I cannot upload a picture when I create a post.

Here is some more background information about my setup. 

I have assign the name and group for all of my folder, located inside my USER/WEBISTE folder to so that everything is owned by www-data:www-data.   I did this because I have been told that wordpress uses the www-data user and group which is the same user and group as Apache2 running on Ubuntu. 

The permission settings for these folders are the following:

USER folder:  Permission= 755, owner = USER:USER
WEBSITE folder:  permission=755, owner = USER:USER
wp-content  folder:  permission= 755,  owner = www-data:www-data
uploads folder: permission =775,  owner = www-data:www-data
2011 folder:  permission=775, owner = www-data:www-data

I am attempting to upload a picture from within wordpress to the USER/WEBSITE/wp-content/uploads/2011 directory.   

I get an error message stating that wordpress cannot create the folder 02.  Check your permission setting for the parent directory.....Apparently Wordpress needs to create a month folder, titled 02 for February, for when you upload a new picture. 

I am stumped on what might be preventing me from creating a folder.   I even attempted to create the folder manually...which was successful.  However, Wordpress did not recognize the new folder.  So I am not sure what is going on.

How do I setup Wordpress so it can create folder, upload files and manipulate the website files?

Can anyone help?

Spindler

---

### Post by lithopsian on 2011-02-05
Set permissions to 777 and see if that helps.  If it does then Wordpress must be writing as someone other than www-data.  If it doesn't then Wordpress would seem to be trying to create a directory somewhere else.

---

### Post by spindler on 2011-02-05
Thanks that is a good point.

When I use 777 I still cannot write to the fill.

It looks like wordpress is writing to a different location... Sorry for not pasted the error message before.  This is what it looks like.

**“Picture.jpg” has failed to upload due to an error**
Unable to create directory /var/www/html/wp-content/uploads/2011/02. Is its parent directory writable by the server?

So it is actually attempting to write into the var directory.

1. Can I change wordpress so it writing into the write directory?
2. Is it better to attempt to change the permissions in the var/html/wp-content director so wordpress can write to that file?

---

### Post by asmoore82 on 2011-02-05
> **spindler said:**
> I have set up VFTP  so I can update my wordpress files using FTP.  I am using the USER name and password to do this.

You should be careful to *only* use authenticated FTP behind your firewall private LAN.
You should **never** have an FTP server that accepts your real passwords from the outside world.

The only FTP that should ever be open to the outside is Anonymous FTP for a
download site or sFTP, which is securely encrypted via the OpenSSH mechanisms.
In fact, to use sFTP all you have to do is install openssh-server.

---

### Post by spindler on 2011-02-06
Hello Asmoore82.

I do not think this information is addressing my problem. 

Do you have a comment on how to fix my permission issue?   I need this issue fixed.

Spindler :cool:

---

### Post by spindler on 2011-02-06
Since wordpress is attempting to write the files to a different directory then i first thought I was thinking maybe the problem is with Apache2.   is there anyway of checking how Apache2 processes this type of request.

Here is what my virtualHOST file looks like.  This is the redirect file for pointing to my website.  It is located in the etc/apache2/sites-available directory.

 <VirtualHost *:80>
    ServerAdmin [email]XXX@XXXX.org[/email]
    ServerName WEBSITE.org
    ServerAlias *.WEBSITE.org

    DocumentRoot /home/USER/WEBSITE
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /home/USER/WEBSITE>
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
        Allow from 1XX.0.0.0/2XX.0.0.0 ::1/XXX
    </Directory>

</VirtualHost>

---

