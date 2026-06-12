---
title: "apache2 won't run/install"
date: 2009-12-31
forum: General Help
---

### Post by ryadav on 2009-12-31
I can't seem to get apache to run? I keep getting the following error

yadav@KubuntuX64:$ sudo /etc/init.d/apache2 start
.: 44: Can't open /etc/apache2/envvars

I have tired to fix this with a reinstall, but I don't see the file 'envvars' ?

the system I am running is:

yadav@KubuntuX64:$ uname -a
Linux KubuntuX64 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

---

### Post by fragos on 2009-12-31
My /etc/apache/envvars:

# envvars - default environment variables for apache2ctl

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

## The locale used by some modules like mod_dav
export LANG=C
## Uncomment the following line to use the system default locale instead:
#. /etc/default/locale

export LANG

---

### Post by fragos on 2009-12-31
My /etc/apache/envvars:

# envvars - default environment variables for apache2ctl

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

## The locale used by some modules like mod_dav
export LANG=C
## Uncomment the following line to use the system default locale instead:
#. /etc/default/locale

export LANG

---

### Post by ryadav on 2009-12-31
something is totally off, now I am getting a 

apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory

so I simple create a empty file using touch, and then tried to start apache and getting more errors

yadav@KubuntuX64:$ sudo /etc/init.d/apache2 start
 * Starting web server apache2apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
no listening sockets available, shutting down
Unable to open logs

---

### Post by ryadav on 2009-12-31
George thanks for you help, but I decided to just build from source. The one built from source seem to be working fine.

---

