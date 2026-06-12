---
title: "Help Setting up Apache?"
date: 2010-02-24
forum: General Help
---

### Post by DaveGiant on 2010-02-24
I have run the following.

> 
    sudo apt-get install apache2

    sudo apt-get install php5

    sudo apt-get install libapache2-mod-php5

    sudo /etc/init.d/apache2 restart


This works, I have php5.2 + apache. Thats fine.

What I need to do is set up mod-rewrite.

I added this line to the http.conf (which is empty - I thought stuff should be in here)

> LoadModule mod_rewrite /usr/lib/apache2/modules/mod_rewrite.so

The path is correct but I get the following error : 

> apache2: Syntax error on line 207 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/httpd.conf: Can't locate API module structure `mod_rewrite' in file /usr/lib/apache2/modules/mod_rewrite.so: /usr/lib/apache2/modules/mod_rewrite.so: undefined symbol: mod_rewrite

I think there is a final step that I am missing. Could someone help me out please.

Thanks.

---

### Post by Halibutt on 2010-03-27
Same problem here, except I installed LAMP with a single sudo command (LAMP is listed as dependencies for Wordpress local installation). 

Any help?
Cheers

---

### Post by kcammack on 2010-03-30
This might be helpful - I think loading mods is different in 2.2 than in previous versions:

[http://articles.slicehost.com/2007/11/23/ubuntu-gutsy-apache-config-layout](http://articles.slicehost.com/2007/11/23/ubuntu-gutsy-apache-config-layout)

---

