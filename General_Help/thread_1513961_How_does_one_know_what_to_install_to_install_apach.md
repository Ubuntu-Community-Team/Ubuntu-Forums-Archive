---
title: "How does one know what to install to install apache"
date: 2010-06-20
forum: General Help
---

### Post by Bucephalus01 on 2010-06-20
Hi

I want to install LAMP on my ubuntu, but I just don't know what packages I would need. Same for PHP. Say if I wanted to installed Apache, how would I know what to put in my sudo apt-get line?
I would think it would be: sudo apt-get apache2 or something like that.
Same with Synaptic, I could look for it and mark it to installed, but there are so many other packages with the word apache in it too, and I'm left wondering, have I got everything?

So where does one find out the exact packages he needs to installed php and apache?
Is this forum the only way to find out via asking, or is there some webpage you can go to that tells you?

DAvid.

---

### Post by WorMzy on 2010-06-20
You can do it package by package if you really want to, but you can just run ```
sudo tasksel install lamp-server
```

EDIT: if you want to do it package by package, then install the following: ```
apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
```

---

### Post by gmargo on 2010-06-20
To get the list of packages with the **tasksel** command:
```

$ tasksel --list-tasks | grep -i lamp
u lamp-server    LAMP server

$ tasksel --task-packages lamp-server | sort
apache2
apache2-mpm-prefork
apache2-utils
apache2.2-bin
apache2.2-common
libapache2-mod-php5
libapr1
libaprutil1
libaprutil1-dbd-sqlite3
libaprutil1-ldap
libdbd-mysql-perl
libdbi-perl
libhtml-template-perl
libmysqlclient16
libnet-daemon-perl
libplrpc-perl
libwrap0
mysql-client-5.1
mysql-client-core-5.1
mysql-common
mysql-server
mysql-server-5.1
mysql-server-core-5.1
php5-common
php5-mysql
ssl-cert
tcpd

```

---

### Post by Bucephalus01 on 2010-06-22
Thankyou both of you.
that has been very helpful.

David.

---

