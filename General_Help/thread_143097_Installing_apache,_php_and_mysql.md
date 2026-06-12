---
title: "Installing apache, php and mysql"
date: 2006-03-11
forum: General Help
---

### Post by ubuntukid on 2006-03-11
I was wondering how I go about installing apache, php and mysql. I couldn`t find apache in either of the package managers.

---

### Post by veratyr on 2006-03-11
This should help

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installapachehttpserver]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installapachehttpserver")

---

### Post by adamkane on 2006-03-11
To install ubuntu-lamp, go here and learn how to add the Sevea repository through source-o-matic:
[http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu")

then 

```

sudo apt-get install ubuntu-lamp

```

or do this:

```

sudo apt-get install apache2 php5 mysql-client-4.1 mysql-server-4.1 php5-mysql libapache2-mod-php5 libapache2-mod-auth-mysql

``` 
If you want to install php4 instead of php5, then just change php5 to php4 above.

---

### Post by pug_205 on 2006-04-10
This may be a bit late to ask (considering I already did the install) but why such an old version of mysql?

---

### Post by chocolatetoothpaste on 2006-04-10
MySQL 5 has been just a hair quirky.  PHP5 as well.  There was a big jump between php4 and php5 and a lot of code broke with the upgrade.  MySQL also had some issues, especially with php5, but most are not critically serious.  Unless there is something very specific to MySQL5 or PHP5 that you need, your best bet is the latest php4 and mysql 4.1.

---

### Post by adamkane on 2006-04-10
Apache2 + PHP4 + MySQL4 + phpmyadmin is stable in Ubuntu.

If you need more functionality, then go ahead and install version 5 from source, but you will likely have installation/maintenance issues. Be sure to ask the forums, if you have any problems.

---

