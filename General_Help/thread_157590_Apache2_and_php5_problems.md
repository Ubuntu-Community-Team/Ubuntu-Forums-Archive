---
title: "Apache2 and php5 problems"
date: 2006-04-09
forum: General Help
---

### Post by ryanakca on 2006-04-09
Hello
I recently installed PHP5 onto apache2, with aptitude, yet I am having trouble with .php webpages.
 I dont get errors in errors.log or anything, but when I try to access php pages on localhost, the server wont display php files, and when you try to access an image, it only gives you the url to the image, and not the image itself. 
I have php5.conf and php5.load in /etc/apache2/mods-enabled.
What's going on?
I am running dapper, and nobody else in #ubuntu+1 seems to know whats wrong.
Thanks in advanced,
ryanakca

EDIT: problem is resolved by installing using the from source versions of apache and php. The topic can be closed now :)

---

### Post by adamkane on 2006-04-09
Apache2 + PHP4 + MySQL4 + phpmyadmin is stable in Ubuntu. To make things easier, see:
[https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP")

It is difficult to install and maintain Apache2 + PHP5 + MySQL5 +phpmyadmin in Ubuntu. If you have much patience, see:
[http://doc.gwos.org/index.php/Latest_Apache_and_PHP]("http://doc.gwos.org/index.php/Latest_Apache_and_PHP")

Once you install a particular version of PHP, it is extremely difficult to install a different version. Choose wisely.

---

### Post by ryanakca on 2006-04-09
aye, Second link, I had installed apache and php5.1 from source a while back, it's still there, except that when I try to install an app that depends off apache, threw apt, apt installs it's own version of apache...
Cheers,
ryanakca

PS: Sorry if I'm kindof unclear...

---

### Post by adamkane on 2006-04-09
LAMP errors are some of the most difficult errors to troubleshoot. After several days of frustration, you will find that it is easier to install LAMP on a clean system.

Your option is to re-install PHP5 from source, and see what happens or install a stable LAMP:
```

sudo apt-get install apache2 php4 mysql-client mysql-server libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql phpmyadmin

```

Sorry for not being very helpful. There are a few people on the forums who may be able to pinpoint your problem, but they can only do that, if you provide more details about the steps you took to install PHP, but there isn't much to go on.

---

### Post by ryanakca on 2006-04-09
Don't worry...  php5 and apache from source works fine, along with ubuntu mysql... its the versions of apache2 and php5 that are in the repositories that don't work for me... I'll post the list of apache / php5 related packages that I installed threw apt... also, is it possible to set apt up to recognise that apache and php5 ARE installed?

---

