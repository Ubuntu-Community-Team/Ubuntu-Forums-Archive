---
title: "Permission problem on /var/www"
date: 2006-03-10
forum: General Help
---

### Post by Tim Thumb on 2006-03-10
I'm trying to set up apache/MySQL/PHP on my new install of ubuntu Breezy with [this wiki]("https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29") as a guide. I'm wanting to run it locally only.

All seems to be working, but I can't work out how to set permissions on the /var/www folder - which I assume is where I place web documents. I can't copy any web docs into it now as I am told I don't have permission when I try.

I understand from the wiki that it's because I'm not logged in as root but when I try to follow the instructions to change this I can't work out what to do:

> Edit Apache Configuration

You may want your current user to be the PHP pages administrator. To do so, edit the Apache configuration file :

$ sudo gedit /etc/apache2/apache2.conf

Search both the strings starting by "User" and "Group", and change the names by the current username and groupname you are using. Then you'll need to restart Apache. (look at the next chapter concerning apache commands) 

I can find one entry for this like:

User www-data
Group www-data

I've tried altering this by adding the name I log in with for User but I have no idea what to put for Group. Any help appreciated.

---

### Post by infoburner on 2006-03-10
Your problem is not the apache configuration, the problem is that the /var/www folder is owned by the root user. If you want to be able to put things directly in the /var/www folder as yourself then type

cd /var
sudo chown username:username www

where username = your login name. This will change the ownership of the www folder to yourself, so you can put stuff in it. I think doing it this way could be considered a security hole though, so the way I do it is to make sub directories of www hold different websites. For example :

cd /var/www
sudo mkdir site_one
sudo chown username:username site_one

Will make the directory /var/www/site_one, which you can then put whatever you want in.

---

### Post by Tim Thumb on 2006-03-10
That worked great - thanks.

---

### Post by Burgresso on 2006-03-16
Infoburner: I'm glad I found your post above. Very helpful.

---

### Post by infoburner on 2006-03-16
glad to help! :-D

---

