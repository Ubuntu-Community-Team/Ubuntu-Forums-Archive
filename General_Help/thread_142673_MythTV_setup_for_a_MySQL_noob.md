---
title: "MythTV setup for a MySQL noob"
date: 2006-03-10
forum: General Help
---

### Post by SadaraX on 2006-03-10
I am trying to setup MythTV for my system:

System Spec's:
> 
MotherBoard: Abit Kt7 Raid
Video Card: ATI All-In-Wonder-Radeon 32MB DDR
Sound: Sound Blaster Live!
CPU: AMD Athlon T-Bird 1200 MHz
RAM: SD-PC-133 512MB
Distro: Ubuntu/Kubuntu 5.10, KDE 3.4.3
Kernel: 2.6.12-9-686-smp
Keyboard: Standard 104-PC key english
Mouse: USB Optical Microsoft Mouse (the really common kind)


I am having problems getting MySQL to work. I know ABSOLUTELY NOTHING about MySQL. I apt-get installed mythtv successfully, which also brought in mysql packages. I run the mythfrontend, it tells me: "Myth could not connect to database. Please verify your database settigs below"

Hostname: localhost
Database: mythconverg
User: mythtv
Password: mythtv
Database Type: MySQL

After I finish, it gives me the console messge: 

> 
2006-03-10 19:37:36.060 Writing settings file /home/clifton/.mythtv/mysql.txt
2006-03-10 19:37:36.062 Writing settings file /home/clifton/.mythtv/mysql.txt
2006-03-10 19:37:36.067 Unable to connect to database!
2006-03-10 19:37:36.067 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)


I am completely confused about what to setup or what to do. I would really appreciate some help for someone who has no idea what to do with MySQL.

---

### Post by andlinux21 on 2006-03-11
Check out this thread 

[]("http://www.ubuntuforums.org/showthread.php?t=106713&highlight=MythTV")

There is a link in the first post that shows a great HOWTO see if that can help you.:mrgreen:

---

### Post by andlinux21 on 2006-03-11
I didnt get the link to post sorry [http://www.ubuntuforums.org/showthread.php?t=106713&highlight=MythTV]("http://www.ubuntuforums.org/showthread.php?t=106713&highlight=MythTV")

---

### Post by SadaraX on 2006-03-11
[QUOTE=andlinux21]I didnt get the link to post sorry [http://www.ubuntuforums.org/showthread.php?t=106713&highlight=MythTV]("http://www.ubuntuforums.org/showthread.php?t=106713&highlight=MythTV")[/QUOTE]

Thanks for that information. Now I have run into another problem (the same problem I have had with a lot of other tutorials on MythTV setup). 

In the "Configure the database (MySQL)", when I open a webbrowser and type "localhost" without the quotation marks into the address bar, it gives me the message "The connection was refused when attempting to contact localhost." 

Any ideas?

---

### Post by andlinux21 on 2006-03-11
Make sure you have apache installed try this

sudo apt-get install apache2 

you should be able to see a page when apache is running

---

### Post by SadaraX on 2006-03-11
I have apache2 installed now, but when I run as root 'invoke-rc.d apache2 start' I get the message:

> 
* Starting web server (Apache2)...
/usr/sbin/apache2ctl: line 78:  9593 Segmentation fault      $HTTPD -k start -DSSL [fail]
invoke-rc.d: initscript apache2, action "start" failed.


---

### Post by andlinux21 on 2006-03-11
try this to restart the apache server

Restart Apache:


Code:
sudo /etc/init.d/apache2 restart

---

### Post by SadaraX on 2006-03-11
[QUOTE=andlinux21]try this to restart the apache server

Restart Apache:


Code:
sudo /etc/init.d/apache2 restart[/QUOTE]


I get the message:
 * Forcing reload of web server  (Apache2)...                            [fail]

So both start and restart do not work...

---

### Post by andlinux21 on 2006-03-11
ok I will have to find out why your apache wont start that is the problem with your localhost once we fix this you should be on your way with MythTV

---

### Post by SadaraX on 2006-03-11
Well, I downloaded and compiled the latest version of apache, version 2.2.0. This compiled just fine but after I installed it, there was no change in the system version. I just ran with the very standard ./configre && make && make install. When I used the ./configure with --prefix=/apache2, I went to the /apache2/bin directory and verified the executable files were of the new version. If I started apachectl from that directory, I can use a webbrowser to go to "localhost" but all I get is the message "It works!"

So, I guess I got apache work, but not really. I will continue to work on this, but if anyone has an idea what I am doing wrong, I would appreciate it.

---

### Post by dc2447 on 2006-03-11
[QUOTE=SadaraX]I get the message:
 * Forcing reload of web server  (Apache2)...                            [fail]

So both start and restart do not work...[/QUOTE]apachectl configtest

---

### Post by warjowuch on 2006-05-16
why on earth does mythtv need a database server and apache...?? I just want to watch tv and eventually record it...

---

### Post by SadaraX on 2006-05-17
[QUOTE=warjowuch]why on earth does mythtv need a database server and apache...?? I just want to watch tv and eventually record it...[/QUOTE]

Eh, its has its features. For the most part, my sql is just fine. It keeps the recording entries, channels, and settings in the database. Apache has some nice web interface features that are pretty nice. 

I ended up using KnoppMyth and besides FluxBox being nothing like what I wanted for a desktop environment, it worked very well. I did have some minor color configuration problems until I set the proper values that I wanted (using the apache web interface no less!)

---

