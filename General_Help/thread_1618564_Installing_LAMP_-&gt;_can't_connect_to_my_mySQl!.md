---
title: "Installing LAMP -&gt; can't connect to my mySQl!"
date: 2010-11-10
forum: General Help
---

### Post by Konbuntu on 2010-11-10
im in the process of installing LAMP. im presently installing mysql and that's where i got into trouble...

im following the this tutorial [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

i tried the following :

Step 3. This is where things may start to get tricky. Begin by typing the following into Terminal:
 

mysql -u root

and i got this output: 

[B]root@konlah-laptop:/home/konlah#  mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/B]

obviously my question is why can't i connect to local mysql?
what would you guys recommend me to do?

thanks in Advance

---

### Post by lmarmisa on 2010-11-10
I think that the service mysql is stopped.

Type this command:

```

sudo service mysql start

```You should get an output similar to:

```

mysql start/running, process 4610

```

---

### Post by Konbuntu on 2010-11-10
thanks!

i just have on last problem 

[B]konlah@konlah-laptop:~$ sudo /etc/init.d/apache2 restart
[sudo] password for konlah: 
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

i tried to restart the web server apache to finalize the tutorial and i got the following problem...


[/B]

---

### Post by lmarmisa on 2010-11-10
Maybe this link could help you

[http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/](http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/)

P.S. Don't forget to install phpmyadmin. It's great!!!.

---

### Post by Konbuntu on 2010-11-10
great!

thank you =)

---

