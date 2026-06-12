---
title: "Another PHP problem :(#$%!!!???"
date: 2006-06-25
forum: General Help
---

### Post by xpix on 2006-06-25
Hello,

I am trying to install php5 for Apache 2 but haven't yet succeeded. I read almost all the Appache2 php5 posts.

Here is what I have done:


Installed Apache2 and libs
Installed php5 and libs
Php does not work(the browser wants to download the php file)

here is what i have done after reinstalling php5(Note: Apache works):

```
___:~$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of apache 2.0 web server...                            [ ok ]

___:~$ man a2enmod
Reformatting a2enmod(8), please wait...

___:~$ ls -l /etc/apache2/mods-enabled
total 0
lrwxrwxrwx 1 root root 36 2006-06-25 20:43 cgi.load -> /etc/apache2/mods-available/cgi.load
lrwxrwxrwx 1 root root 40 2006-06-25 20:43 userdir.conf -> /etc/apache2/mods-available/userdir.conf
lrwxrwxrwx 1 root root 40 2006-06-25 20:43 userdir.load -> /etc/apache2/mods-available/userdir.load

___:~$ sudo a2enmod php5
This module does not exist!

```

So, I installed php5 and libs through Synaptic, restarted Apache but as you can see php5 is not available as a module for Apache2

I will try to install php as cgi.

Until then maybe there is an answer.

Thank You

---

### Post by scxtt on 2006-06-25
how exactly are you trying to access your *.php file through the browser? ... i just put apache2 + php5 on my xubuntu VM and it worked w/o me doing anything special at all ... i put an index.php file in /var/www and pointed my browser (on the ubuntu host, 192.168.1.100) to the VM's IP address (192.168.1.101) and it parsed the PHP perfectly, which was a simple:

[PHP]<?php echo "this is a php test." ?>[/PHP]i have seen/had the problem you're mentioning before - and i think the solution for me was to add .php to a line in the config file that tells apache to parse .php files like it does w/ .pl (or .cgi) files ... but i didn't need to do that w/ apache2+php5 ...

---

### Post by xpix on 2006-06-26
Hi,

I use to access the page: 
[http://localhost/index2.php](http://localhost/index2.php)
[http://192.168.0.3/](http://192.168.0.3/)
etc

Code inside index2.php from var/www
```

<? phpinfo() ?>
<?php echo "this is a php test." ?> 
```


I will try the solution you mentioned.

Thx

---

### Post by xpix on 2006-06-26
Hi, I found the problem :D 

in /etc/apache2/mods-enabled i created a file called **php.load** with the following line:

```
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

...and it worked

Can someone confirm that a file like I created is necesary and it was created via Synaptic.

Thx

---

### Post by scxtt on 2006-06-26
that's weird you had to do anything extra - i was able to put "<? phpinfo() ?>" in my index.php and it worked fine ...

---

### Post by vhof on 2007-08-22
Hi I can confirm that after installing with apt-get install , i had the same problem.
The thing is, in my case it still doesn't work :) ))

---

### Post by heimo on 2007-08-22
Did you guys install libapache2-mod-php5 package?

---

### Post by j.stagner on 2007-08-25
I am just writing to confirm that I also had this problem, and creating a file  containing the following line worked for me to resolve the issue.

** /etc/apache2/mods-enabled/php.load**
```
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

---

