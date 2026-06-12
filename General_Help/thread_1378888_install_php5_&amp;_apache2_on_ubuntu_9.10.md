---
title: "install php5 &amp; apache2 on ubuntu 9.10"
date: 2010-01-12
forum: General Help
---

### Post by creatxr on 2010-01-12
version ubuntu 9.10

after I used package manager to install php5 and apache2,
I copied my php files to /var/www
and I use command "sudo /etc/init.d/apache2 restart" to restart apache2

but when I visit my php files, 

I put "info.php" to /var/www , it works.
but, when i visit the other php files in the directory under "/var/www" (e.g. /var/www/mydir) , the browser want to download them.
this "mydir" is moved by command "mv mydir /var/www".

what's the problem?
thanks.

---

### Post by creatxr on 2010-01-12
i found that 'mv ./mydir/mydir ./mydir/otherdir', the php files could run.
so i run 'sudo chmod 777 ./mydir/mydir' 
but it is useless.
how can i do

---

### Post by fragos on 2010-01-12
Create /etc/apache2/httpd.conf with the following three lines or add them if the file already exists. These lines enable PHP execution.

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

