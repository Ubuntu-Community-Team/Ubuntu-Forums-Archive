---
title: "apache2 config file is broken"
date: 2012-02-28
forum: General Help
---

### Post by cybercity@localhost on 2012-02-28
my apche config file is broken and i can't start apache on my server. I've tried to reinstall apache but it's still not working?

---

### Post by greenpeace on 2012-02-28
Come on... give us a little more to work with!! :)  

What is the error when you start the Apache server?  

Post the command you're using and the error you get when you start the server!

---

### Post by cybercity@localhost on 2012-02-28
> **greenpeace said:**
> Come on... give us a little more to work with!! :)  

What is the error when you start the Apache server?  

Post the command you're using and the error you get when you start the server!

this is what i get when i attempt to start apache server

.: 49: Can't open /etc/apache2/envvars

while my webmin interface outputs

>  The Apache configuration file /etc/apache2/apache2.conf does not exist. If you have Apache installed, adjust the [module configuration]("https://cybercity.net:10000/config.cgi?apache") to use the correct path.

---

### Post by greenpeace on 2012-02-28
This question seems to be describe your problem pretty closely, can you have a look at it and see how you get on?

[http://askubuntu.com/questions/26228/how-can-i-replace-missing-configuration-files-after-removing-a-package]("http://askubuntu.com/questions/26228/how-can-i-replace-missing-configuration-files-after-removing-a-package")

---

### Post by Elrond1369 on 2012-03-22
To resolve this and return Apache/Webmin back to defaults:1. Login as root
2. apt-get purge apache2.2-common
3. apt-get purge apache2
4. apt-get clean
5. apt-get install apatche2
do this to fix webmin
1. apt-get purge webmin 
2. apt-get clean
3. apt-get install webmin

---

### Post by Habitual on 2012-03-22
got backup?

---

