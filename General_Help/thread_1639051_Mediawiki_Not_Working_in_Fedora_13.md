---
title: "Mediawiki Not Working in Fedora 13"
date: 2010-12-06
forum: General Help
---

### Post by Serpher on 2010-12-06
I'm trying to get Mediawiki to work on Fedora 13, but I'm running into a few problems. I've tried to install this in two different ways so if you know how to fix either problem, let me know. The site is in /var/www/html/wiki/:


1: 'yum install mediawiki' method (sudo apt-get install mediawiki)

After installing I've managed to get it to run but it keeps giving me a Forbidden Error. I've enabled the proper booleans on SELinux and I've looked at file/directory permissions and nothing's helped. I've even edited my httpd.conf so 'Options FollowSymLinks' is 'Options FollowSymLinks includes'. I'm not really sure what most of this means but I've just been following what other people have been saying on forums.


2: I downloaded the .tgz from the wikimedia site, however when I try to run the file to setup wikimedia I just get PHP code instead of a page produced by the PHP. I realized PHP wasn't installed so I installed it via yum (apt-get for Fedora) but it still helped none.



I know this is an Ubuntu forum but a Linux is a Linux is a Linux right

---

### Post by Slim Odds on 2010-12-06
> **Serpher said:**
> ...

I know this is an Ubuntu forum but a Linux is a Linux is a Linux right

No, actually it's NOT.

Ubuntu is based on Debian, Fedora it based on Red Hat. They are very different.

Ubuntu uses apt-get, Fedora uses yum. They are very different.

I would highly recommend the Fedora forums: [http://forums.fedoraforum.org/](http://forums.fedoraforum.org/)

---

### Post by polki@mac.com on 2010-12-07
Mac OS X is 7.6? Windows 7 is really Windows 95? A troll is serious? I am helpful right now? (Sorry about that, but I tend to get angry at some stuff..)

---

