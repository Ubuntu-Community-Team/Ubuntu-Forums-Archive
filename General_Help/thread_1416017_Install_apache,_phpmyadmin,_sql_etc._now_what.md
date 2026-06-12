---
title: "Install apache, phpmyadmin, sql etc. now what?"
date: 2010-02-25
forum: General Help
---

### Post by realn00b on 2010-02-25
Ok, so earlier on windows, i used to test my websites and different forum scripts using WAMP SERVER. I read that post earlier which said that we can install all those components individually on ubuntu and start using them. I used following command to install all of them:
```
sudo apt-get install php5 mysql-server apache2 phpmyadmin
```

Everything got installed properly, i setup passwords for few things. And now if i type "localhost" in browser, heres what i get:-
**```
It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.
```


I presume, it means that everything is installed properly. Now i want to know, where exactly is this directory to upload the files that i want to test. like the www directory? And also how can i access the phpmyadmin?

Thanks.

---

### Post by PoHandle on 2010-02-25
The default www directory is at **/var/www** .  That's the root web directory on my server where I upload my pages to.

I don't use phpmyadmin, but according to [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin) , you should be able to go to [http://localhost/phpMyAdmin/scripts/setup.php](http://localhost/phpMyAdmin/scripts/setup.php)  and work from there.

---

### Post by realn00b on 2010-02-25
> **PoHandle said:**
> The default www directory is at **/var/www** .  That's the root web directory on my server where I upload my pages to.

I don't use phpmyadmin, but according to [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin) , you should be able to go to [http://localhost/phpMyAdmin/scripts/setup.php](http://localhost/phpMyAdmin/scripts/setup.php)  and work from there.


Ok great, thanks i found that WWW dir that i was talking about and thats solved.

But your answer for phpmyadmin doesnt solve the problem. my main motive to use phpmyadmin is to create and delete databases often as i am going to be testing some blog and forum scripts locally.

---

### Post by PoHandle on 2010-02-25
Did you include /etc/phpmyadmin/apache.conf in your apache2.conf?

Make sure the line ```
Include /etc/phpmyadmin/apache.conf
```
is in /etc/apache2/apache2.conf

If it's not there, add it, save, then restart apache
```
sudo /etc/init.d/apache2 reload
```

---

### Post by realn00b on 2010-02-25
Ok i  edited that file, saved it and restarted the whole thing.

Still when i try to access localhost/phpmyadmin, it says "The requested URL /phpMyAdmin/ was not found on this server.". 

So whats the exact way of opening phpmyadmin in a browser?

---

### Post by realn00b on 2010-02-25
Ok... if i do "127.0.0.1/phpmyadmin" it works. it takes me to the login page. But m not sure if i was asked to create a username at the time of installation. I use same password for everything, so i think my password wud work... but how abt the username?

---

### Post by PoHandle on 2010-02-25
The default username is **root** and there is not default password, so leave that blank.

---

### Post by realn00b on 2010-02-25
GREATTTT!

NOw i think i know and understood everything that m supposed to including changing the permissions.... so thanks so much for your help PoHandle.

---

