---
title: "/var/www"
date: 2009-08-01
forum: General Help
---

### Post by cancer10 on 2009-08-01
Hi people


First of all I am new to Linux.

I installed LAMP with the following command

apache2 php5-mysql libapache2-mod-php5 mysql-server

from the tuotorial [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


All works well, but now I want to create a new file or delete the index.html file from /var/www

Why wont it let me delte that file? I see the delete option disabled and so is the create new document option


Pls help

---

### Post by lavinog on 2009-08-01
most likely you don't have permission to modify the file.
there are various ways to work around this, one being editing the file as root.
```
gksu gedit /var/www/index.html
```
others involve changing the owner or changing the permissions.
you can change the owner
```
sudo chown username /var/www/index.html
```
I don't think changing the owner on this file affects anything, but there are some files you don't want to do that to.

I believe it is better to set the owner to be the same as what apache is set to run as. On my setup it is www-data.
```

>cat /etc/apache2/envvars
# envvars - default environment variables for apache2ctl

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

```

---

### Post by cancer10 on 2009-08-01
When I installed ubuntu it asked to select a user/pass to login...does not that makes me the root?

---

### Post by lavinog on 2009-08-01
> **cancer10 said:**
> When I installed ubuntu it asked to select a user/pass to login...does not that makes me the root?

It adds you to the sudoers list, but does not mean that you are root. In fact root logins are disabled in Ubuntu for security reasons.

I would suggest reading [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
If you are planning on setting up a webserver that will be accessible from the internet, I would strongly recommend understanding ownership and permissions also.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html#http-configuration](https://help.ubuntu.com/8.04/serverguide/C/httpd.html#http-configuration)

Is your webserver going to be accessible from the internet, or are you just experimenting with it?
Pay attention to security. Sometimes the simpler/quickest solutions can open doors for hacking.
If you install a webapplication (forums, image gallery...etc) keep up with updates. Bots scan the internet for all webservers, testing out known security holes.  Review your logs frequently. Usually you will see a bunch of file not found errors (favicon not found errors are caused by firefox, and don't mean anything. They be fixed by making a favicon for you site)

The www-data user exists so you don't need to run apache as root (very bad things can happen if you do.)
Setting your website files to be owned by www-data would be preferred instead of having them owned by root.
Turn off the writable bit on files that don't need to be writable. And turn off the executable bit on files that don't need to be executed.

---

### Post by yogi4 on 2009-08-01
type in teminal-

sudo nautilus

go to /var/www do whatever u wanna do wid ny filr

---

### Post by cancer10 on 2009-08-03
> **yogi4 said:**
> type in teminal-

sudo nautilus

go to /var/www do whatever u wanna do wid ny filr

Hi

Thanks for your post. Can you please tell me what will that command do?

Also, when I run this command (apache2 php5-mysql libapache2-mod-php5 mysql-server) I have 4 questions about it:

1) Where does apache gets installed?
2) Where does php gets installed?
3) Where does mysql gets installed?
4) if I want to install an extension for PHP, say Mbstring or GD (assuming they are not installed)?


Thanks

---

### Post by yogi4 on 2009-08-03
all of them r installed in /etc directory

---

### Post by cancer10 on 2009-08-03
> **yogi4 said:**
> all of them r installed in /etc directory


ok but you didnt tell me what does that command **sudo nautilus** do?

---

### Post by credobyte on 2009-08-03
For GUI stuff, use gksudo, not sudo:
```
 
gksudo nautilus /var/www/

```
 
What it does is opens up a Nautilus window ( file manager ) with root privileges ( every single file outside your home directory is owned by root and you can't edit them that easily ).

---

### Post by cancer10 on 2009-08-03
Thanx for the info :)

Loving Ubuntu :)

---

