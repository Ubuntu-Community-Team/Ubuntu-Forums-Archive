---
title: "LAMP with Perl"
date: 2012-03-11
forum: General Help
---

### Post by srikrishnan on 2012-03-11
Hi all,

In my Ubuntu 11.10 OS, I have installed LAMP successfully as per mentioned in the following article "Install LAMP and phpMyAdmin on Ubuntu 11.10" from the following site "http://tuxtweaks.com/2011/10/install-lamp-and-phpmyadmin-on-ubuntu-11-10/". 

Everything works perfectly, all my php files are successfully opened in my firefox browser. But i am not able to see my cgi and pl files in my web browser. 

I want to configure perl in my Apache to run cgi and pl files.

Is it possible for somebody to help me in fixing this issue?

Thanks in Advance,
Srikrishnan

---

### Post by 2F4U on 2012-03-11
Shouldn't be too difficult:

[http://www.blog.highub.com/perl/install-configure-apache-localhost-perl-on-linux-ubuntu/](http://www.blog.highub.com/perl/install-configure-apache-localhost-perl-on-linux-ubuntu/)
[http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html)

---

### Post by srikrishnan on 2012-03-12
Hi,

I have already tried as per mentioned in the first link.

Eventhough, when i browse cgi files it shows the coding in the browser, when i browse pl files, it asks me to download the file.

I dont know what can I do to fix this issue

Below is my installed procedure as per mentioned in the link

srikrishnan@srikrishnan-System-Product-Name:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

srikrishnan@srikrishnan-System-Product-Name:~$ sudo apt-get install libapache2-mod-perl2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-perl2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
srikrishnan@srikrishnan-System-Product-Name:~$ sudo gedit /etc/apache2/apache2.conf
srikrishnan@srikrishnan-System-Product-Name:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
srikrishnan@srikrishnan-System-Product-Name:~$ sudo gedit /etc/apache2/apache2.conf
srikrishnan@srikrishnan-System-Product-Name:~$ sudo /etc/init.d/apache2 restart * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
srikrishnan@srikrishnan-System-Product-Name:~$ 


Thanks,
Srikrishnan

---

