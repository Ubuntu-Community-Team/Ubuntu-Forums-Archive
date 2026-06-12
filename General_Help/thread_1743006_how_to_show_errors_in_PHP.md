---
title: "how to show errors in PHP?"
date: 2011-04-29
forum: General Help
---

### Post by ayet on 2011-04-29
iam using ubuntu 10.04 apache2 mysql php5 i develop php pages, i want to be able to show errors on my page, its disabled some how, how to you enable it in ubuntu? i understand theres php.ini in windows but what about ubuntu?

---

### Post by cokicd on 2011-04-29
> **ayet said:**
> iam using ubuntu 10.04 apache2 mysql php5 i develop php pages, i want to be able to show errors on my page, its disabled some how, how to you enable it in ubuntu? i understand theres php.ini in windows but what about ubuntu?

Try this

```
sudo gedit /etc/php5/apache2/php.ini
```Look for this line

```
display_errors = Off
```Replace it with

```
display_errors = On
```Save

Done

---

### Post by dragonfly41 on 2011-04-29
I'm migrating my php development from Vista to ubuntu.

as explained in last post (from cokicd) start by choosing the error reporting level in php.ini

[http://php.net/manual/en/errorfunc.configuration.php](http://php.net/manual/en/errorfunc.configuration.php) 

.......

Optionally ..

You can go on to install Xdebug module for PHP 5 .. php5-xdebug 2.1.0-1 in Synaptic Package Manager.

Then restart Apache2 and check by running phpinfo.php that Xdebug is enabled.

......

I've also installed eclipse (Galileo) and the Aptana Studio 3 eclipse plugin.

Use web perspective in eclipse for php development.

But this is a *major installation* and you might prefer a lighter weight development environment for PHP.

In which case try jEdit and various plugins.

---

