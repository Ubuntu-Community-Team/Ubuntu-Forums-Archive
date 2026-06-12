---
title: "I need help with PHP and VirtualBox please help"
date: 2009-10-29
forum: General Help
---

### Post by TRUJohn on 2009-10-29
Ok this is my first post withing these forums.  And before i ask for help i would like to congratulate you all for a job well done.  But lets get to work,  I have 2 problems which i cannot solve at all, i read books, i looked on the web but nothing worked, i am not saying that the advice was not good all i am saying is that i cant make it work.

Problem number 1-  I installed Ubuntu 9.04 and i installed apache2 mysql and php5 but unfortunatly i cannot see any PHP in the browser.  I think i instaled ubuntu at least 5 times in the past day, dont get me started on LAMP.  Can someone please help me make php apache and mysql work in harmony in unbuntu, and yes i did find a lot of posts but IT DOSENT WORK, so i want to uninstal everything and reinstall it properly will someone please help me?

Problem number 2 -  Ok i installed Virtual Box because i needed a windows emulator for the Adobe CS4 master edition, unfortunatly for me i cannot share files betwen the virtual machine and ubuntu client i think its called.  I found some posts on the internet about this but i cannot make it work i always stop at the end.  

Please people have mercy on a beginer and give me a hand because i really love ubuntu, and i hate windows.

---

### Post by chipper_farley on 2009-10-29
You need to make sure you've installed the correct apache and php modules (you may have...just not sure from your post) in order for apache to work with PHP and MySQL.  If you're not sure, do:

sudo apt-get install libapache2-mod-php5
sudo apt-get install php5-mysql

Once you do that, you should be good.  Check the config files for apache (located at /etc/apache2/apache2.conf) and for php (/etc/php.ini I think) and make sure you're setup correctly.  I've been using PHP with MySQL and Apache for almost 10 years now and whenever I setup a new server, I usually have to fiddle with it for a while to get it to work, even today.  You can get it going as this is one of the most common setups there is in Linux.

---

### Post by TRUJohn on 2009-10-29
I will do what you said and give it another go, i am kind of beginner with all of this linux php apache mysql, so if you could give me something to look for in the config file that would be appreciated

---

### Post by chipper_farley on 2009-11-02
The main apache config file will be in the /etc/apache2 directory and called apache2.conf.  It's a really long and complex file.  Usually though you have a sites-available and sites-enabled directory in the same place.  The sites-available directory will have any sites that get created by a package, like Squirrelmail or WordPress.  Anything that you want to have be live, just create a link in the sites-enabled directory.  There's a default file in the sites-available directory you can use as a template.

As for PHP, just locate the PHP.ini file...that's the only one.  There's lots of options in there but you'll see that the file is really well commented.  I think you can go to PHP's website and get a sample production file that is a little more secure than what is installed by default.

Installing the packages I mentioned above should link in PHP to Apache and allow PHP to talk to MySQL just by installing them so really all you'll need to do is drop in your php files in the /var/www directory or wherever you setup in a new file in sites-available and you'll be off and running.

---

