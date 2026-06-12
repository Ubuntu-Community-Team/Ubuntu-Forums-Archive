---
title: "Apache VH"
date: 2010-09-05
forum: General Help
---

### Post by zurek22 on 2010-09-05
hello Ubuntu lovers,

let me get straight to the point here im looking for assistance on setting up virtual hosting with no-ip dynamic DNS servers, i have absolutely no idea how to do this i have tried to do the research but i keep messing up and having to reformat the hard drive and reinstall Ubuntu.

im running Ubuntu 10.04


i wanna run 2 websites

just ask me what u need and ill give it to you

thank you
zurek22

---

### Post by zurek22 on 2010-09-05
I need Help ="(

---

### Post by sandyd on 2010-09-05
> **zurek22 said:**
> hello Ubuntu lovers,

let me get straight to the point here im looking for assistance on setting up virtual hosting with no-ip dynamic DNS servers, i have absolutely no idea how to do this i have tried to do the research but i keep messing up and having to reformat the hard drive and reinstall Ubuntu.

im running Ubuntu 10.04


i wanna run 2 websites

just ask me what u need and ill give it to you

thank you
zurek22
```

sudo apt-get install lamp-server ddclient
```

---

### Post by zurek22 on 2010-09-06
> ```
sudo apt-get install lamp-server ddclient
```well i already have a client similar to that, the no-ip client is the one, i guess its cause i wasn't clear enough about what i needed

i need help with getting apache to do 2 virtual hostings one for one website and the other for another website, no-ip has a how-to but i don't understand all of it, the website is [here ]("http://www.no-ip.com/support/guides/web_servers/using_apache_virtual_hosts.html")
i'm still quite new at the Linux things.

---

### Post by sandyd on 2010-09-06
> **zurek22 said:**
> well i already have a client similar to that, the no-ip client is the one, i guess its cause i wasn't clear enough about what i needed

i need help with getting apache to do 2 virtual hostings one for one website and the other for another website, no-ip has a how-to but i don't understand all of it, the website is [here ]("http://www.no-ip.com/support/guides/web_servers/using_apache_virtual_hosts.html")
i'm still quite new at the Linux things.

[http://webmin.com](http://webmin.com)

---

### Post by sandyd on 2010-09-06
> **carlee said:**
> [http://webmin.com](http://webmin.com)

remember to firewall yourself so that port 10000 is not accessable from the internet

---

### Post by zurek22 on 2010-09-06
alsome this is what i was looking for thank you so much, now my question is how do i configure no-ip to look at the virtual hosts

---

### Post by sandyd on 2010-09-06
> **zurek22 said:**
> alsome this is what i was looking for thank you so much, now my question is how do i configure no-ip to look at the virtual hosts
easy.
In webmin (note, this is from memory,as I don't run ubuntu)
Navigate to
[http://localhost:10000](http://localhost:10000)
login
go to servers -> apache 

Create a new virtual host for your no-ip address

If you could give me a screenshot of the "add new virtual host" page, I can likely help you better.

---

### Post by bradleyd on 2010-09-06
Are these virtual hosts ip based or name based?

---

### Post by zurek22 on 2010-09-06
ok i cant restart apache in this program and if i modify anything in the program and try to restart i get an error

```
administrator@ServerHome:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                 [ OK ] 
administrator@ServerHome:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                        apache2: Syntax error on line 236 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory
                                                                                                 [fail]
administrator@ServerHome:~$ 

```

i dont understand what is going on here

---

### Post by zurek22 on 2010-09-06
ok i fixed it, i had to recreate the file, and set the permissions to root

---

### Post by zurek22 on 2010-09-06
ok so i fixed my last screw up and now i cant do this i need help i keep getting this error now

```
administrator@ServerHome:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                        [Mon Sep 06 22:41:53 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Mon Sep 06 22:41:54 2010] [warn] NameVirtualHost *:80 has no VirtualHosts

```

i hate this can anyone help me fix this in webmin?

---

### Post by zurek22 on 2010-09-08
continued to [http://ubuntuforums.org/showthread.php?t=1570199](http://ubuntuforums.org/showthread.php?t=1570199)

---

