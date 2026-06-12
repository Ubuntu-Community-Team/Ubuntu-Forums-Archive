---
title: "APT-GET and packing peanuts"
date: 2006-05-23
forum: General Help
---

### Post by yusufm on 2006-05-23
Hi,

I wanted to get phpmyadmin to administer mysql. I did a search and found this:

[http://packages.ubuntulinux.org/breezy/web/phpmyadmin](http://packages.ubuntulinux.org/breezy/web/phpmyadmin)

It says that it is in the universe repository. I had some noob questions about this.

1) Is the universe repository controlled by ubuntu? What I mean is that someone can't just go and add the myphpadmin package into it right, it has to come from the legitimate source that makes myphpadmin. (what i'm afraid of is someone loading up a compromised package into the repository). (this does not have to deal with popular things either, lets say, someone uplaoded myhacky package, and if i come across it, I want to make sure someone has verifired it.)

2) If I install a package like myphpadmin from apt-get, it should automatically install updates? And do these updates correspond to those that are released by the project team? Or are the patches only distributed when someone has compiled and uplaoded to the respository? (I'm concerned about security vulnerabilities that are fixed by phpmyadmin team, not getting to me immediately as it is released).

---

### Post by _linux_ on 2006-05-23
Don't worry, the Universe repository is a legitimate, community-controlled repository for Ubuntu. As for the updates, they're installed just like any other updates. And yes, the updates probably correspond to those made by the project team, but aren't supported as much as those in the main repository. So the phpmyadmin installation will go smoothly with Synaptic and apt-get. Good luck!

---

### Post by 23meg on 2006-05-23
> 1) Is the universe repository controlled by ubuntu? What I mean is that someone can't just go and add the myphpadmin package into it right,That's right.

> 2) If I install a package like myphpadmin from apt-get, it should automatically install updates? And do these updates correspond to those that are released by the project team? Or are the patches only distributed when someone has compiled and uplaoded to the respository? (I'm concerned about security vulnerabilities that are fixed by phpmyadmin team, not getting to me immediately as it is released).Packages in Universe aren't guaranteed to have official security updates. Those in Main are.

---

### Post by yusufm on 2006-05-24
I was looking to get the apache2 package from universe, but it says the latest version is 2.0.5.xxxx whereas the newest one on apache.org is 2.2.2. Isn;t there a way to apt-get the latest version of apache straight form apache.org?? 


[QUOTE=23meg]That's right.

Packages in Universe aren't guaranteed to have official security updates. Those in Main are.[/QUOTE]

---

### Post by adamkane on 2006-05-24
[SIZE=3]It's best to have a stable apache/php/mysql. If you try to install all the latest from source, you will have issues, and no one to help you.

Stick to this, and be glad I got to you early:[/SIZE] 

[SIZE=3]Apache2/PHP4/MySQL4 (breezy or dapper):
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

If you need the latest, then you may want to find a linux distribution that has those versions:
[http://www.distrowatch.com]("http://www.distrowatch.com")
[/SIZE]

---

