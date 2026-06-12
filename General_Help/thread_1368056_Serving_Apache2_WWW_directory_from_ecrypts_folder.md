---
title: "Serving Apache2 WWW directory from ecrypts folder"
date: 2009-12-30
forum: General Help
---

### Post by utkjamie on 2009-12-30
My home directory is encrypted using ecryptfs. I am running Apache2 on my computer as a development server for my web projects. I want to be able to keep Apache's document root in my home folder instead of the default /var/www. The problem is that ecryptfs denies access to the webserver (user: www-data) and all pages come up with a 403 error.

I seem to recall that I was able to grant access permissions to the root user when I setup my encrypted home directory. This allows the root user to access my encrypted files whenever I am logged on. Is there a way to grant www-data access to one specific folder in the same way?

---

### Post by lucidwayn on 2010-01-18
have you tried changing the user and group in apache2.conf file to run as your user instead of "www"?

::apache2.conf
[INDENT]# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}[/INDENT]



actually the variables are stored in /etc/apache/envars

::envars
[INDENT]# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
#export APACHE_RUN_USER=www-data
#export APACHE_RUN_GROUP=www-data
export APACHE_RUN_USER=USERNAME
export APACHE_RUN_GROUP=GROUPNAME[/INDENT]

would be great to know if you managed to run the server from an encrypted folder.

---

### Post by mirsal on 2010-03-10
@lucidwayn It works, and it saved my day, thanks.
However, I'm still looking for a less kludgy solution, so if anyone has an idea...

---

### Post by fonfi on 2010-06-24
Forcing apache to run as USER instead of www-data gives it access to encrypted folder as long as USER remains logged on. After logging out, apache stops serving data stored in encrypted folder. Is there any way to make it work whenever USER is logged on or out?

---

