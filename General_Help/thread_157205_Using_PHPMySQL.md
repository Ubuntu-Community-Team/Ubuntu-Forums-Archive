---
title: "Using PHP/MySQL"
date: 2006-04-08
forum: General Help
---

### Post by ubuntukid on 2006-04-08
I have a book on PHP and MySQL and I want to start learning how to use it. I was therefore wondering if someone could point me to an article which explains how to set up PHP and MySQL (and probably Apache as well) so that I can start doing this.

---

### Post by Noah0504 on 2006-04-08
I suggest using XAMPP for Linux: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html).

It's very easy setup.  All you have to do is extract and run.  If you ever decide to remove it, you just delete the directory.

---

### Post by adamkane on 2006-04-08
Apache2 + PHP4 + MySQL4 + phpmyadmin is very easy to install on Ubuntu:
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

You can install Apache2 + PHP5 + MySQL5 + phpmyadmin on Ubuntu, but you have to install from source.

XAMPP is overkill if you're starting out. There is no way to maintain all the included packages over time. Use XAMPP, if you need all the included packages, and you intend to install XAMPP on its own server.

---

