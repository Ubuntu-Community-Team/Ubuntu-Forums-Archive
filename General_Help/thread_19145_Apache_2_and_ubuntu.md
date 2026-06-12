---
title: "Apache 2 and ubuntu"
date: 2005-03-10
forum: General Help
---

### Post by motu on 2005-03-10
hi all,

i've tried to install apache 2 with synaptic (it also installs the common and mpm-worker packages) and then i've a directory called Apache2 in /etc/.
my problem comes...
when i want to start apache (/etc/init.d/apache2.dpkg-new start) :

 * Starting web server (Apache2)...
 *ache2: could not open document config file /etc/apache2/apache2.conf   [fail]

neither the apache2.conf or httpd.conf exist but i've got apache2.conf.dpkg-new

i'm lost.

please help me!

---

### Post by lightyear on 2005-03-11
I'v got a similar problem, if i try to start the server PREFIX/bin/apachectl start i get a mesage no such file or directory. The same if i want to alter the config file with "vi PREFIX/conf/httpd.conf".  When i test the server i get the apache default page...so obviously the server is running.  What am i doing wrong here? how can i alter my config file?

I am a newbie to linux so i slowly trying to work out what is happening within linux etc. i worked out where my www root directory is, but when i try to copy my website to this directory i get an no permisions to write to this directory message. 
I am logged in as the user that i created when installing....i presume this got admin rights so i am a bit confused on how to set permissions on this specific directory.

Thanks a lot in advance

Bas

---

