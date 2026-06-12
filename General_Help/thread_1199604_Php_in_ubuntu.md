---
title: "Php in ubuntu"
date: 2009-06-29
forum: General Help
---

### Post by mahroof on 2009-06-29
I am a php programmer, i am working in WINDOWS platform  . Now i wish to change my platform to ubuntu, please help me .

---

### Post by mcduck on 2009-06-29
Install Ubuntu, install LAMP-server, start working.

If you want more precise help you'll have to tell us what you need help with. :)

---

### Post by snek on 2009-06-29
I suggest using [Zend Server CE]("http://files.zend.com/help/Zend-Server-Community-Edition/zend-server-community-edition.htm#deb_installation.htm"), it is possibly the easiest LAMP stack you can install and is much faster in general than a bog standard LAMP installation. Lots of information is available as well.

I have installed it on various workstations & servers.

After you add the correct lines to /etc/apt/sources.list it's as easy as:
sudo aptitude install zend-ce php5-extra-extensions-zend-ce phpmyadmin-zend-ce

Be sure to login to the admin screen after installing and turning off the PHP components you **don't** need..

The admin section is usually found at this url: [https://127.0.0.1:10082/](https://127.0.0.1:10082/)
****

---

### Post by cpetercarter on 2009-06-29
Read [this]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

### Post by mcduck on 2009-06-29
> **snek said:**
> I suggest using [Zend Server CE]("http://files.zend.com/help/Zend-Server-Community-Edition/zend-server-community-edition.htm#deb_installation.htm"), it is possibly the easiest LAMP stack you can install and is much faster in general than a bog standard LAMP installation. Lots of information is available as well.

I have installed it on various workstations & servers.

After you add the correct lines to /etc/apt/sources.list it's as easy as:
sudo aptitude install zend-ce php5-extra-extensions-zend-ce phpmyadmin-zend-ce

Be sure to login to the admin screen after installing and turning off the PHP components you **don't** need..

The admin section is usually found at this url: [https://127.0.0.1:10082/](https://127.0.0.1:10082/)
****

I doubt it would be easier than using Ubuntu's own LAMP:

```
sudo tasksel install lamp-server
```

---

### Post by kokkus on 2009-06-29
If you use Dreamweaver in windows, you can still use it in Ubuntu by in ubuntu by installing the program WINE. This is a program that will let you use (some) windows programs in Ubuntu.
Then when you have installed Wine, install Dreamweaver in ubuntu.
Good luck :)

---

### Post by snek on 2009-06-30
Installation is not the only part of the process.. The default lamp stack still needs quite some configuration to be suitable for the specific server. Zend doesn't need that so much tbh, I have it running on a 256mb Ubuntu VPS and it greatly outperforms the default install.

As an editor I suggest Zend Studio. It's available for Win/Lin/Mac...

---

