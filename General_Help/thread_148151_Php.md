---
title: "Php"
date: 2006-03-21
forum: General Help
---

### Post by shiznatix on 2006-03-21
Ok so I install apache2, php 5 and the mysql librarys. I was then looking for a mysql administration program and installed phpmyadmin without reading the 'this will be uninstalled'. Then phpmyadmin gave me a heck of a lot of trouble and I was finally able to uninstall it but then my PHP was broken. I used Synaptic to uninstall everything dealing with PHP and apache but then when I re-installed PHP no longer works, it just asks me to download the file. I have restarted apache2 many times without anything changing.

How can I get PHP 5.0 with mysql and GD support working on apache2? I can do a fresh install so if I have to uninstall anything that is fine.

Thanks if you can help me out.

---

### Post by KingBahamut on 2006-03-21
[http://doc.gwos.org/index.php/Latest_Apache_and_PHP](http://doc.gwos.org/index.php/Latest_Apache_and_PHP)

Hope this helps.

---

### Post by shiznatix on 2006-03-21
that looked promising but once again, no cigar. Is there any way to make sure that everything is 100% uninstalled with PHP and apache? I am 99% confident that mysql is not the problem because everything was working perfect until the stupid phpmyadmin problems and I bet that if I get everything off my hard drive and start from scratch ill be golden.

Anyone else? Is there no walk through to do this easily? Seams to be too difficult to be true because this was quite easy in windows.

---

### Post by harisund on 2006-03-21
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

This is something you might want to read, just make sure you change all the PHP4 references to PHP5 and you will be fine (trust me !)

---

### Post by harisund on 2006-03-21
Oh and I forgot, do you have a GUI installed? If so, you can fire up synaptic which would make your life easier. 

Just open synaptic, and search for apache, then for php and then for mysql, and simply remove (purge) everything you find. You will be as good as new.

---

### Post by shiznatix on 2006-03-21
*sigh* PHP is STILL not working. It is weird because it says to download a PHTML file and not  PHP file when you go to it (normally it says download a PHP file if I am not mistaken). Why oh why? Apache works just fine though, but why not PHP?

Just so you know, I am not very good with this stuff and things like fixing config files by hand is not my specialty. Is there somthing somewhere that might make this strange behavior happen?

Synaptic says that php5, php5-common, and php5-mysql are all installed.

edit: harisund, I am using Synaptic for this...

---

### Post by harisund on 2006-03-21
First, have you customized any of Apache / PHP / MySql configuration files? 

If you have not, here is something I might suggest you try out .. 

Firstly, go ahead and start removing everything. And I mean purging. Sort of something like this.
apt-get --purge remove apache2 apache2-common php5 php5-common libapache2-mod-php5 php5-gd

Of course, the last one if you have gd module enabled only. 

When the above is done, just do
apt-get install apache2 php5 
And things should automatically work. Regarding mysql, we will see that later once your php is working. 

Read my post on this thread here
[http://ubuntuforums.org/showthread.php?t=105107&highlight=apache2-common](http://ubuntuforums.org/showthread.php?t=105107&highlight=apache2-common)

And you can read this thread when you are free. 
[http://ubuntuforums.org/showthread.php?t=108191&highlight=mysql+php](http://ubuntuforums.org/showthread.php?t=108191&highlight=mysql+php)

And do post back if you could get it to work .. 

Hari

---

