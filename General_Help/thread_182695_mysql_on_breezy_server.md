---
title: "mysql on breezy server"
date: 2006-05-26
forum: General Help
---

### Post by bodemiller on 2006-05-26
Hello,
I am trying to install mysql on breezy server. I installed mysql on  a separate breezy desktop machine using instructions from 5.10 starter guide:
sudo apt-get install mysql-server
which worked fine on breezy desktop box. I get 404 for apt-get sources for breezy server.
apt-get sources are:
desktop: us.archive.ubuntu.com
server: security.ubuntu.com
sources.list files look identical. Any reason why the server would go to different source?
Thanks for your help,
Bode

---

### Post by binks on 2006-05-31
could you tell me how the box connects to the net ie 
direct 
thro a proxy 
on an intranet
cheers binks

---

### Post by bodemiller on 2006-06-02
It is direct connection to internet, through a linksys box.:)

---

### Post by bodemiller on 2006-06-02
"sudo apt-get update" worked

problem solved:)

---

### Post by adamkane on 2006-06-07
Technique to install mysql:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

