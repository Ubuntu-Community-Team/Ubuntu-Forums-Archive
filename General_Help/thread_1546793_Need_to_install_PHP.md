---
title: "Need to install PHP?"
date: 2010-08-05
forum: General Help
---

### Post by wenfuli on 2010-08-05
Running Lucid, if I want to do some work with PHP, do I need to install it first or is it already there? (If it is there, I can't find it.) If I do need to install, how exactly do I do that? I did a search for PHP in Synaptic, but I had no idea what exactly I should be installing.

---

### Post by bbkingwithaj on 2010-08-05
I just posted a question about remotely the same thing.

Try this in your cmd line:
```

sudo apt-get install php5
```

if it says you need to install something, you didn't have it
otherwise it will just tell you it's already there

---

### Post by uylug on 2010-08-05
What sort of things are you attempting to do? If you're going to make a website you'll also need to have apache installed.

---

### Post by lisati on 2010-08-05
To answer the question in the thread title: No thanks, I don't need to because I already have it installed. :D

As others have pointed out, what you can (should?) install depends in part on what you want to do. I have a command-line version installed on my laptop, and another version installed on my web server that is more suited to working with web pages.

---

### Post by wenfuli on 2010-08-05
To be totally honest, I'm not exactly sure what I'm trying to do, or at least, it's hard to be specific. I'm just getting started with PHP. That is, I'm trying to learn it and so I need something that will allow to practice using it.

---

### Post by abhot on 2010-08-05
[SIZE=3]If you want to learn php you should install LAMP server.
It contains everything you need..[/SIZE]
[COLOR=#000000][SIZE=3][FONT=Liberation Serif]a)sudo apt-get install lamp-server^ 
[/FONT][/SIZE][/COLOR][SIZE=3][COLOR=#000000][FONT=Liberation Serif]b)then give MySQL root password 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]c)test apache by typing in the web browser  [http://localhost/](http://localhost/)   you will 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]see a window which says it works 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]d)test php. You'll need to create a file in /var/www called testing.php 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo nano /var/www/testing.php [/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]Enter the following line into the text editor, save the file and exit 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]<?php phpinfo(); ?> 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]Next, restart Apache with the following terminal command: 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo /etc/init.d/apache2 restart 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]Now go back to your web browser and enter the address 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]http://localhost/testing.php/ 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]You should see a page displaying version information for your 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]php installation[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]e)Configure MySQL 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]Since I'm installing LAMP for a web development environment, I want[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]the MySQL database to be bound to the localhost IP address. This[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]should be 127.0.0.1 for your system. You can verify it with this 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]terminal command 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]cat /etc/hosts | grep localhost 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]You'll now want to verify that the correct bind address is set up 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]in MySQL's my.cnf file 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]cat /etc/mysql/my.cnf | grep bind-address 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]You should see a line that looks like this:  bind-address= 127.0.0.1 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]f)Install phpMyAdmin 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]You don't need to install phpMyAdmin, but it's a much easier way to 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]get in and adjust things in your MySQL database if you're not 
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]
[/FONT][/COLOR][/SIZE] 
  [SIZE=3][COLOR=#000000]   [FONT=Liberation Serif]familiar with MySQL's commands. You can install phpMyAdmin from 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]the command line with: 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]sudo apt-get install libapache2-mod-auth-mysql phpmyadmin 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]The installation will prompt you to select a web server for 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]automatic configuration.This is important! Use the space bar on 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]your keyboard to select apache2 and then hit <Enter> 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]then bla bla bla hit <enter>[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]then you will be prompted to enter your enter your MySQL root password 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]& phpmyadmin application password 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]then bla bla bla <enter> your are done 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]g)Testing phpMyAdmin 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]Open your web browser and enter the address [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]You can log in with the username root and the root password that you 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]created earlier 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]Congratulations, you're now ready to start building your local website.[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]If you're only working on one site you can put all of your files into 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif]/var/www.  If you'll be working on multiple sites you may want to 
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]consider some additional Apache configuration to keep things neat[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Liberation Serif]and clean on you system. 
[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Liberation Serif][SIZE=4]How to run php scripts-->[/SIZE][/FONT][/COLOR][/SIZE]
[COLOR=#000000][FONT=Liberation Serif][SIZE=3]PHP code is executed on the server, and the plain HTML result is sent to[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif][SIZE=3]the browser 
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]sudo nano /var/www/filename.php 
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif][SIZE=3]then rum from the browser 
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif][SIZE=3]http://localhost/filename.php [/SIZE][/FONT][/COLOR] 
  
[SIZE=3]Hope this helps:popcorn:
[/SIZE]

---

### Post by v1ad on 2010-08-05
the reason u need to install the whole server is because you won't be able to preview php files without a generator. aka the web server.

---

### Post by wenfuli on 2010-08-05
abhot: I'm at work right now so I'm not exactly free to check that out to see if it works, but thanks in advance. 

One question for now (probably more to come later): How long did it take you to type that all out? :-)

---

### Post by lisati on 2010-08-06
> **v1ad said:**
> the reason u need to install the whole server is because you won't be able to preview php files without a generator. aka the web server.

Minor correction: php5-cli can be run on the command line without apache or a browser, and can be used to test code snippets which don't need to be rendered as web pages.

From [https://help.ubuntu.com/8.04/serverguide/C/php5.html:](https://help.ubuntu.com/8.04/serverguide/C/php5.html:)
> You can run PHP5 scripts from command line. To run PHP5 scripts from command line you should install php5-cli package. 

---

### Post by uylug on 2010-08-06
> **lisati said:**
> Minor correction: php5-cli can be run on the command line without apache or a browser, and can be used to test code snippets which don't need to be rendered as web pages.

From [https://help.ubuntu.com/8.04/serverguide/C/php5.html:](https://help.ubuntu.com/8.04/serverguide/C/php5.html:)
Indeed. Php-cli can be run as a standalone package. You can test your scripts but won't be able to create a web site.

If you're going to get started in PHP, you should install lamp. It's much more user friendly, productive and effective to see things.. in a browser... and design stuff.

---

