---
title: "accidently deleted php* from /usr/local/bin"
date: 2010-01-15
forum: General Help
---

### Post by hvshah69 on 2010-01-15
I accidently executed "rm /usr/local/bin/php*" command. I believe I deleted at least php and php-cgi.

How do I reinstall these files? apt-get install php5 does not seem to do it

Ubuntu server edition 9.04

---

### Post by rjl6591 on 2010-01-15
The proper location is /usr/bin - the system will never install anything under /usr/local. (The /usr/local heirarchy is specifically intended to be a place the OS packaging tools leave alone.)

Try purging the packages and reinstalling them, i.e.

sudo apt-get purge php5 php5-cgi
sudo apt-get install php php5-cgi

---

### Post by hvshah69 on 2010-01-15
Well, I am trying to manually compile php with php-fpm support. After successfully compiling php source, when I try to start *php-fpm start*, I get an error saying that it cannot find /usr/local/bin/php (since I accidently deleted it).

Also, same with any PECL commandline operations. For example, *pecl install memcache* also is expecting /usr/local/bin/php. 

So, I am not sure what to do now

---

### Post by pbrane on 2010-01-15
Why don't you simply **make install** again? That will re-install the missing files. Or you can run **make uninstall** and re-configure with **--prefix=/usr** and then install. That will install the files to /usr/bin and so on.

---

