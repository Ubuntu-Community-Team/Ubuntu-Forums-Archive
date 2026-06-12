---
title: "tomcat7 installation problem"
date: 2011-11-15
forum: General Help
---

### Post by aaronfromchina on 2011-11-15
Tomcat 7 doesn't work after I remove some tomcat7 configuration files. How can I fix it?

Initially, I installed Tomcat7 by the command:
```
sudo aptitude install tomcat7
```
then I removed /etc/tomcat7 directory accidentally.
Now I can't recover tomcat7. I've tried
```
sudo aptitude remove tomcat7
sudo aptitude install tomcat7

```
I'd like to reinstall tomcat7, so I remove /etc/init.d/tomcat. but it doesn't help.

The error message of installing tomcat7 is following:
sudo aptitude install tomcat7
The following NEW packages will be installed:
  libtomcat7-java{a} tomcat7 tomcat7-common{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/3,441 kB of archives. After unpacking 4,518 kB will be used.
Do you want to continue? [Y/n/?] y
Preconfiguring packages ...              
Selecting previously deselected package libtomcat7-java.
(Reading database ... 143522 files and directories currently installed.)
Unpacking libtomcat7-java (from .../libtomcat7-java_7.0.21-1_all.deb) ...
Selecting previously deselected package tomcat7-common.
Unpacking tomcat7-common (from .../tomcat7-common_7.0.21-1_all.deb) ...
Selecting previously deselected package tomcat7.
Unpacking tomcat7 (from .../tomcat7_7.0.21-1_all.deb) ...
Processing triggers for ureadahead ...
Setting up libtomcat7-java (7.0.21-1) ...
Setting up tomcat7-common (7.0.21-1) ...
Setting up tomcat7 (7.0.21-1) ...
chmod: cannot access `/etc/tomcat7/tomcat-users.xml': No such file or directory
dpkg: error processing tomcat7 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 tomcat7
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tomcat7 (7.0.21-1) ...
chmod: cannot access `/etc/tomcat7/tomcat-users.xml': No such file or directory
dpkg: error processing tomcat7 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tomcat7

---

### Post by t_gra on 2012-03-18
I have this problem too.
Looks like something left from tomcat that causes "configure" to misbehave.

---

### Post by dragonfly41 on 2012-03-18
I kept a tomboy note for installing tomcat7 manually.. not from *.deb ..  into /usr/share/tomcat7/

refer to helpful guide here ...

[http://diegobenna.blogspot.com/2011/01/install-tomcat-7-in-ubuntu-1010.html](http://diegobenna.blogspot.com/2011/01/install-tomcat-7-in-ubuntu-1010.html)

edit environment variables in /etc/environment/

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
CATALINA_HOME="/usr/share/tomcat7"
CATALINA_BASE="/usr/share/tomcat7"
JAVA_HOME="/usr/lib/jvm/jdk1.7.0"
JRE_HOME="/usr/lib/jvm/jdk1.7.0/jre"


your java vars might vary from my setup

then of course you have to setup config files

---

