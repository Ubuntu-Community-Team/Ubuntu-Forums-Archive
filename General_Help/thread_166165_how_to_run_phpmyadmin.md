---
title: "how to run phpmyadmin?"
date: 2006-04-25
forum: General Help
---

### Post by medya on 2006-04-25
i want to install mythTV , by this tutorial
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

it says :
[QUOTE=the tutuorial site]MythTV uses MySQL extensively, so we have to get this set up before anything else. Fire up Firefox and in the address bar, type "localhost". Click the "phpmyadmin" directory.... [/QUOTE]

when I open firefox and enter localhost, it is like it goes forever and nothign happens... what should I do ?

---

### Post by rvergara on 2006-04-25
Is apache running in your PC?

Check system, administration, services and check that apache is actually running as a service.

Regards

Ramiro

---

### Post by Toxicity999 on 2006-04-25
Install apache2 and everything that goes with it along with phpmyadmin (It's in the repos I believe.) If you don't have a local web server running it's rather hard to connect to =P. If you do have it installed and such, sorry for wasting your time.

---

### Post by Zorro on 2006-04-25
If you have ***apt-get install mythtv*** and have mysql installed, it will set the db up for you automagically.. I run mythtv, and didnt have to muck around with any db settings...

---

### Post by medya on 2006-04-26
i I nstalled the Apache an Mysql4 and PHP4 by the wiki
[https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=ApachePHPMySQL](https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=ApachePHPMySQL)

but it wont run anything when I enter [http://127.0.0.1/](http://127.0.0.1/) or localhost in the browser .


I guess I have done some things wrong in the installation, infact there was some parts of the wiki which was confusing and I guessed it and did it by guessing like these parts.

like this part
> 
Installing MYSQL 4

$ sudo apt-get install mysql-server
$ sudo apt-get install libapache2-mod-auth-mysql
$ sudo apt-get install php4-mysql

If you want a powerfull and easy graphical interface:

$sudo apt-get install phpmyadmin

[COLOR="Red"]But remember to choose and set a phrase for cryptography in the file /etc/phpmyadmin/blowfish_secret.inc.php and copy the line (not the php tags) into the file /etc/phpmyadmin/config.inc.php or you will receive an error.[/COLOR] 

by the way I checked the System/admin/services and both Apache and Mysql were checked .

---

### Post by Toxicity999 on 2006-04-26
Thats pretty strange... normallly on installing even just apache you get some kind of a welcome message. try gettign to it though local host, or your actual Ip on the port you have apache set to.

---

### Post by medya on 2006-04-30
please help me, at least tell me how I can un-install everything ? that I did by UBUNTU WIKI
and tell me a safe easy way to install an apache server on my linux ...

---

### Post by jamesdodd on 2006-04-30
When I installed myth through apt-get it was a nightmare!

I now have the failed attempt to setup the database on anythin I do with apt-get... anyway...

You shouldnt install apache unless you want to run a webserver... if its just for setting up mysql then its a wasted resource...

you should be able to just run "mysql" from terminal login with root and your root password and then copy the content of the myth tv sql file (its located in either ~/.mythtv or /usr/shared/mythtv or somethin)

I had to then run sudo mythsetup or something...

I've never used myth since cos its pretty crap and the lack of a decent TV app is why I'll be moving back to windows

---

### Post by medya on 2006-04-30
I do need Apache Sever, I want to try some PHP files, without uploading them to internet

---

### Post by rvergara on 2006-04-30
medya,

if apache is actually running (you can verify this in the system monitor and see if you a process named apache2 running or sleeping), the only thing i can think it may be a problem is that you are not listening in the default port (80).

You can check this by opening your ports.conf file in /etc/apache2,it should have a line such as:

Listen 80

You can change it to 80 if you have a different number , however you have to stop and restart your apache server in order to take the new configuration. Alternatively you can read the web default page without changing the port by typing:

localhost:yourport

Where yourport is the number you have in the Listen statement in the ports.conf.

If everything else fails you can use synaptic to delete your php/mysql installation and start all over again.

I installed PHP5, mysql 4 and myphpadmin directly from synaptic and i was running my web server in 10 minutes. Use the versions that are tagged with the small ubuntu icon if available.

I hope this helps

Ramiro

---

### Post by medya on 2006-04-30
I reinstalled them by synaptic , the port is 80 ,

I tried localhost:80 in my browser , it doesnt work . it says it is connecting but it wont connect.

---

### Post by rvergara on 2006-05-01
we would need a bit more info in order to debug this.

Please open a system monitor (under application->system tools), go to the processes tab and look for at least one (there may be more than one, that is ok) instance of a process named apache2 running, go to the right most part of the entry and copy its running arguments (should be something like /usr/sbin...). Please post either those arguments or report if you do not find an entry.

go to /var/log/apache2/error.log and copy and paste a few of the most recent entries after a web read attempt.

Post here what subfolders you have under the path /var/www

Regards

Ramiro

---

### Post by medya on 2006-05-01
1-
/usr/sbin/apache2 -k start

2-
> PHP Warning:  Function registration failed - duplicate name - mysql_connect in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_pconnect in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_close in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_select_db in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_query in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_unbuffered_query in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_db_query in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_list_dbs in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_list_tables in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_list_fields in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_list_processes in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_error in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_errno in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_affected_rows in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_insert_id in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_result in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_num_rows in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_num_fields in Unknown on line 0


3-

here are the subdir s :

apache2-default
phpmyadmin

---

### Post by rvergara on 2006-05-01
please post again a few entries of /var/log/apache2/error.log but do not try to read phpmyadmin just try to read localhost. The ones you sent are attempts to execute sql statements but your issue is with apache (at least for the time being).

have you tried to replace localhost with your pc ip (e.g. 192.168.0.1) when trying to display a web page?

Regards

Ramiro

---

### Post by medya on 2006-05-01
[Sun Apr 30 05:53:58 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/4.4.0-3ubuntu2 configured -- resuming normal operations
[Sun Apr 30 06:26:52 2006] [notice] caught SIGTERM, shutting down

---

### Post by medya on 2006-05-01
and here are more errors ...
> PHP Warning:  Function registration failed - duplicate name - mysql_tablename in Unknown on line 0
PHP Warning:  Function registration failed - duplicate name - mysql_table_name in Unknown on line 0
PHP Warning:  mysql:  Unable to register functions, unable to load in Unknown on line 0
[Mon May 01 00:33:04 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/4.4.0-3ubuntu2 configured -- resuming normal operations
[Mon May 01 00:39:21 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 04:45:33 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon May 01 04:45:36 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 04:45:39 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 04:49:13 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 04:51:28 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 04:56:56 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 04:56:58 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 06:33:36 2006] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?
[Mon May 01 06:33:36 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 06:36:21 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 06:36:22 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 06:36:53 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 06:36:54 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 06:37:34 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 06:37:35 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 06:40:44 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 06:41:24 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 08:03:38 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 08:03:42 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 12:41:57 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 12:43:31 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 12:45:52 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 12:46:45 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 14:01:30 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 14:02:08 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 14:06:48 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 18:30:41 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 18:30:43 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 19:11:47 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 01 19:14:40 2006] [notice] caught SIGTERM, shutting down
[Mon May 01 20:06:02 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations

---

### Post by medya on 2006-05-03
so what should I do ...

---

### Post by SreckoMicic on 2006-05-03
I think that you are trying to start php (or Apache) which is ALREADY started. Uninstall one version and try again.
Think this help :-k

---

### Post by medya on 2006-05-03
please tell me a good way to install an APCHE-MYSQL-PHP .

the tuturoial on the ubuntu WIKI wasnt good for me.

---

### Post by SreckoMicic on 2006-05-03
Use Xampp.
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)
But you must uninstall alredy installed apache, php and mysql. Try with synaptic, find it, and check for removal.

---

### Post by medya on 2006-05-03
when I try to remove phpmyadmin I get this error 

E: phpmyadmin: subprocess pre-removal script returned error exit status 127

---

### Post by medya on 2006-05-03
I solved the problem onf PHPMYADMIN's not being removed by this topic 
[http://www.ubuntuforums.org/showthread.php?p=812381](http://www.ubuntuforums.org/showthread.php?p=812381)

---

### Post by medya on 2006-05-04
thanks xampp was insatlled very beuitifully and so relax, 
can u just tell me where to uplod my php files to run ?

there should be a WWW folder, which I can find...


thanks again . UBUNTU WIKI should write this usefull program in their WIKI .

---

### Post by SreckoMicic on 2006-05-04
htdocs folder

---

### Post by medya on 2006-05-04
god damn this MythTV , i tried to install it , and now again my Apache, php , mysql doesnt work... God damn Mythtv

---

### Post by medya on 2006-05-04
I unistalled the mythtv, and unistalled xampp , and reinsatlled it , and still  doesnt work

---

### Post by medya on 2006-05-04
here is my error log you may can help me ,,, I tried to re-install xampp but it doenst work ...
> 
fred@ubuntu:~$ tail -2 /opt/lampp/logs/error_log
[Thu May 04 17:21:40 2006] [warn] RSA server certificate CommonName (CN) `localh ost' does NOT match server name!?
[Thu May 04 17:21:40 2006] [notice] Apache/2.2.0 (Unix) DAV/2 mod_ssl/2.2.0 Open SSL/0.9.8a PHP/5.1.2 mod_apreq2-20050712/2.1.3-dev mod_perl/2.0.2 Perl/v5.8.7 co nfigured -- resuming normal operations


---

### Post by medya on 2006-05-05
Ping . help plz.

---

### Post by medya on 2006-05-05
please somebody help me... I am in pain , I need apache and PHP

---

### Post by medya on 2006-05-06
if nobody can help , I am gonna re-install my ubuntu

---

### Post by medya on 2006-05-07
ok I am going to reinsall ubuntu just to make Apache work ,
can just tell me where I can download that New ubuntu ,  Dapper dake or whatever its name is... 

should I install that or I better install my Breezy Badger?

---

### Post by SreckoMicic on 2006-05-07
Well tell me in detail what is happening with your's Apache or Xampp installation.

---

### Post by medya on 2006-05-07
I installed it Xampp. it worked well , I tried to install mythTV , and then it stopped working.

when I run localhost , it goes forever and wont respond.

---

### Post by SreckoMicic on 2006-05-07
what is mythTV? What is his relevance to Xampp?
where did you install xampp?
Open services and see is there is started Apache service?

---

### Post by phenolholic on 2006-08-09
Hello,
I'm following Hyams HOWTO of installing MythTV. In the part that mentions opening up 'localhost' from browser and changing password, and after trying to go into the 'phpmyadmin' directory, I get:

Cannot load mysql extension. Please check your PHP configuration. - Documentation

I ignored this, and kept on with the installation. After loading mythtv-setup, I get a Database Configuration menu, which says 'Myth could not connect to your database. Please verify the correct information' 
asking me for my login, password, host name, database, and database type. On the /home/mythtv/.mythtv/mysql.txt file, this is the information on there:

DBHostName=localhost
DBUserName=admin
DBPassword=
DBName=mythconverg
DBType=QMYSQL3

I tried going into mythtv-setup and putting in admin and leaving the passwd field blank on that database configuration menu, but no luck.

I also tried:
mysql -u root

and got the mysql> prompt and entered:
SET PASSWORD FOR admin = PASSWORD('mythtv');

and got this response:
ERROR 1133 (42000): Can't find any matching row in the user table

I've verified the services are running and indeed Apache2 and MySQL both are running. Any help would be appreciated. Thanks in advance

---

