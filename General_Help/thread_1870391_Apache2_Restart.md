---
title: "Apache2 Restart"
date: 2011-10-27
forum: General Help
---

### Post by Brooksy_FC on 2011-10-27
Hey All,

I've I'm trying to restart Apache2, but when I enter /etc/init.d/apache2 restart, it comes up saying No such file or directory. I've also tried it with /etc/apache2 and still nothing. Also tried it with sudo first.

Can anyone help?

---

### Post by lisati on 2011-10-27
Try this:
```
sudo service apache2 restart
```

---

### Post by Brooksy_FC on 2011-10-27
Thanks for the quick response. Tried it and came up with...

> Apache2: Could not reliably determine the severs' fully qualified domain name, using 127.0.0.1 for ServerName.

Would that have worked?

---

### Post by WorMzy on 2011-10-27
```
sudo restart apache2
```

is the "correct" way of restarting deamons (since Ubuntu currently uses Upstart), but Lisati's method should work, and you should still have /etc/init.d/apache2. Make sure that you have apache2.2-common installed.

---

### Post by Brooksy_FC on 2011-10-27
There is a apache2 file in the init.d folder. But there is also a apache2 folder in etc/

Everything I try either says no command found or no such directory

---

### Post by shubham1 on 2011-10-27
> **Brooksy_FC said:**
> Thanks for the quick response. Tried it and came up with...



Would that have worked?
same problem came with me but i fixed it by this

---

### Post by shubham1 on 2011-10-27
> **shubham1 said:**
> same problem came with me but i fixed it by this
If you get this error: 
*apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for [ServerName]("https://help.ubuntu.com/community/ServerName")* 
then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to create a new file, 
sudo nano /etc/apache2/conf.d/fqdnor 
gksu "gedit /etc/apache2/conf.d/fqdn"then add 
ServerName localhostto the file and save.  This can all be done in a single command with the following: 
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

---

### Post by shubham1 on 2011-10-27
> **shubham1 said:**
> If you get this error: 
*apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for [ServerName]("https://help.ubuntu.com/community/ServerName")* 
then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to create a new file, 
sudo nano /etc/apache2/conf.d/fqdnor 
gksu "gedit /etc/apache2/conf.d/fqdn"then add 
ServerName localhostto the file and save.  This can all be done in a single command with the following: 
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
i would like to suggest to all who want to setr up apache that
read the guide it would be helpfull

---

### Post by alco75 on 2011-10-27
That Apache warning can also be removed by editing the file **/etc/apache2/httpd.conf** and adding the line **ServerName localhost**.

---

