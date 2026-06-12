---
title: "install virtuemart in ubuntu"
date: 2010-02-11
forum: General Help
---

### Post by urd on 2010-02-11
hi, i have my lamp server whit joomla 1.5 working on ubuntu 9.10 ... and i want to install VirtueMart complement for joomla, but i cant, anyone can help to install it??

thanks!!!

---

### Post by colobix on 2010-02-11
Ok first, set the directors to 777.

chmod 777 component directory
chmod 777 modules directory
chmod 777 plugins directory
chmod 777 administrator directory.


Change php.ini in the following way.

upload_max_filesize = 10M
memory_limit 32M

add the following lines:

php_value memory_limit 64M
php_value register_globals off
php_value max_execution_time 600

save file.

rename the htaccess.txt file in the joomla directory to .htaccess

restart apache by typing the following commands.

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

install component.

Now before you click go directly to store or install sample data go to the command prompt and type the following commands in the joomla directory.

chmod 777 components/com_virtuemart
chmod 777 administrator/components/com_virtuemart 

Now click go directly to store or install sample data.

And it should be installed.

You can now change the administrator and components directories back to 755 permisions.

Hope this helped you.

---

### Post by n0dix on 2010-02-11
Try with this: [http://www.heltech.se/index.php/en/knowledge-base/12-web/24-joomla-virtuemart-installation-problem](http://www.heltech.se/index.php/en/knowledge-base/12-web/24-joomla-virtuemart-installation-problem)

---

### Post by urd on 2010-02-11
how i change the php.ini??

---

### Post by n0dix on 2010-02-11
> **urd said:**
> how i change the php.ini??

sudo nano /etc/php/php.ini

---

### Post by urd on 2010-02-11
thanks finally get it!!

---

### Post by wataru junior on 2011-05-20
> **urd said:**
> thanks finally get it!!
I'm still get the error...
I can't install the package, when i click the install button, i get this message
"There was an error uploading this file to the server."
"Unable to find install package"

Can you tell me step by step to install it?
I used and installed XAMPP for Linux (called lampp) in /opt/lampp

and install Joomla 1.6 in /opt/lampp/htdocs/joomla

and I'm using Ubuntu 10.04....


Thank You before....

---

