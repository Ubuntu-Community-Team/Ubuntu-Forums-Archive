---
title: "How can I upgrade my LAMP server?"
date: 2006-02-18
forum: General Help
---

### Post by XtremeGamer99 on 2006-02-18
I set my server up by downloading the packages. Right now, I have these versions of the software:

Apache: 2.0.54 (Ubuntu)
PHP: 5.0.5-2ubuntu1.1
MySQL: 4.0.24_Debian-10ubuntu2-log


Now, I don't have a problem with the Apache version. But I need to upgrade my PHP and MySQL. I need PHP 5.1, and MySQL 5.

I don't know how to download these from the Synaptic Package Manager --  I can't find them. So, I am guessing I have been forced to download the source from the respective websites. However, I've always had a problem installing things like this manualy. They always screw up, somehow...

I was wondering if anyone can provide step-by-step instructions on how I can upgrade...

Also, I need MySQLi to work. I never got it working when I was running Windows, and I've shied away from it since. But now I would like for it to work, so I need to know how to install it.

Oh, and the way my server is set up is the way the packages set it up. Example, my root web directory is /var/www. My apache configurations is in /ect/apache2, my PHP configuaration is /ect/php5, and so on. I had no option to choose the directories, and I've grown cutom of these directories -- if possible, I'd rather them stay the same with the upgrade...

Thanks to anyone that helps...

---

### Post by XtremeGamer99 on 2006-02-18
Bump.

---

### Post by XtremeGamer99 on 2006-02-19
Bump... Again...

---

### Post by dudus on 2006-04-10
There is a package made by  George. Works fine here

[http://www.untitledproject.co.uk/packages/](http://www.untitledproject.co.uk/packages/)

---

### Post by adamkane on 2006-04-10
LAMP latest for Ubuntu:
[http://doc.gwos.org/index.php/Latest_Apache_and_PHP]("http://doc.gwos.org/index.php/Latest_Apache_and_PHP")

Apache2 + PHP4 + MySQL4 is stable on Ubuntu. If you need more recent packages, you're in an unsupported area. Please share, if you learn anything.

You many want to install XAMPP.

---

### Post by Kresten Kjaer on 2006-04-10
mysql 5 is in dapper and so is php5. Maybe it is time to upgrade ?

---

### Post by adamkane on 2006-04-10
Tough call. Depends on what you need. 

Pros: LAMP, Beagle, MonoDevelop, Gnome deskbar, faster kernel, easier wireless setup.

Cons: Many Breezy applications aren't available for Dapper yet.

I use Breezy, and have Dapper, LAMP and MonoDevelop installed on a spare laptop.

---

