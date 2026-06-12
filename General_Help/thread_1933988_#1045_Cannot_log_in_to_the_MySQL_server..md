---
title: "#1045 Cannot log in to the MySQL server."
date: 2012-03-01
forum: General Help
---

### Post by Brooksy_FC on 2012-03-01
I tried to change my password to my server, but when I try and log in I keep getting this error.

> 1045 Cannot log in to the MySQL server.

I've tried all combinations of users and passwords and having no luck. Anyone have an experiences with this error or know how to get past it?

---

### Post by Tiganjero on 2012-03-01
Try resetting your password with:
```

sudo /etc/init.d/mysql stop
sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
mysql -u root mysql
FLUSH PRIVILEGES;
USE mysql UPDATE user SET Password = PASSWORD('newpwd') WHERE Host = '%' AND User = 'root';
FLUSH PRIVILEGES;
#and relaunch with
sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start

```
Note that *Host = '%'* means that root is able to connect from anywhere, which should be *Host = 'localhost'*, in case you only wish it to be able to connect from localhost. See if that helps.

Cheers,
George

---

### Post by Brooksy_FC on 2012-03-05
Thanks for the reply, all is going well with what you suggested, but I've got too "#and relaunch with" and I wasn't sure what you meant by this.

Do I need to type this or just a comment?

Thanks,
Ryan

---

### Post by Brooksy_FC on 2012-03-05
By the way, I've kinda new too all this. :P

---

### Post by baumanno on 2012-03-05
That's merely a comment, the following lines:
```

sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start

```
ensure that mysql service is really stopped, and then starts it again.

---

### Post by Brooksy_FC on 2012-03-05
Cool, thank you. Did all the code, but got this error.

phpMyadmin - Error

Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.

Any idea what this is?

---

### Post by baumanno on 2012-03-05
What webserver are you running? If its Apache, please do the following:

To find the logfile
```

locate error.log

```

Then copy/paste whatever this spills out:
```

cat path/to/logfile

```

(for reference, my error.log is at /var/log/apache2/error.log if that helps)

---

### Post by Brooksy_FC on 2012-03-05
I've got LAMP installed. I've found the log file. What do you want me to do with 

> cat path/to/logfile

Sorry for all the questions :P

---

### Post by baumanno on 2012-03-05
> **Brooksy_FC said:**
> I've got LAMP installed. I've found the log file. What do you want me to do with 



Sorry for all the questions :P

No Problem :D

Just replace **/path/to/logfile** with the path to your logfile as found by *locate*. The *cat* command should display that file in the terminal-window. Then copy the output into this forum using the CODE-Tags (hidden behind the #-symbol in the editor-toolbar)

---

### Post by Brooksy_FC on 2012-03-05
Ok, I've entered that code and this is what I get back:

```
ryan@ryan-Latitude-D830:~$ cat /var/log/apache2/error.log
[Tue Feb 28 11:38:16 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Tue Feb 28 12:47:13 2012] [notice] caught SIGTERM, shutting down
[Tue Feb 28 12:48:15 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Tue Feb 28 12:50:45 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Tue Feb 28 13:05:21 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_connect(): Access denied for user 'host'@'localhost' (using password: YES) in /var/www/Index.php on line 9, referer: http://localhost/
[Tue Feb 28 13:14:09 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_connect(): Access denied for user 'root'@'localhost' (using password: YES) in /var/www/Index.php on line 9, referer: http://localhost/
[Tue Feb 28 13:46:34 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19, referer: http://localhost/
[Tue Feb 28 13:46:36 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 13:46:54 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 13:46:54 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 13:46:55 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 13:47:18 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 13
[Tue Feb 28 13:47:19 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 13
[Tue Feb 28 13:55:15 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 13:55:17 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 14:29:16 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 14:29:17 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 14:29:18 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 14:29:19 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 14:29:21 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 14:29:22 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/Index.php on line 19
[Tue Feb 28 14:56:12 2012] [error] [client 127.0.0.1] PHP Warning:  mysql_connect(): Unknown MySQL server host 'root@localhost' (1) in /var/www/Index.php on line 12
[Tue Feb 28 15:41:16 2012] [notice] caught SIGTERM, shutting down
[Wed Feb 29 10:41:12 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 29 11:31:38 2012] [notice] caught SIGTERM, shutting down
[Wed Feb 29 11:32:40 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 29 11:41:56 2012] [notice] caught SIGTERM, shutting down
[Wed Feb 29 11:41:57 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 29 15:03:12 2012] [notice] caught SIGTERM, shutting down
[Wed Feb 29 15:26:59 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 29 15:44:59 2012] [notice] caught SIGTERM, shutting down
[Thu Mar 01 10:26:33 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Thu Mar 01 15:10:13 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Mar 01 15:10:17 2012] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected $end in /var/www/insert.php on line 3, referer: http://localhost/
[Thu Mar 01 16:51:59 2012] [notice] caught SIGTERM, shutting down
[Mon Mar 05 09:47:50 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations
[Mon Mar 05 09:57:38 2012] [notice] caught SIGTERM, shutting down
[Mon Mar 05 09:58:40 2012] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.6 with Suhosin-Patch configured -- resuming normal operations

```

---

### Post by baumanno on 2012-03-05
Apart from a coupla false logins last week that seems okay. It might be as simple as just clearing your browser-cache, so please do that (clear all cookies, delete temporary files, the whole lark) and report back. Also, ensure that cookies are enabled in your browser.

If you feel comfortable in doing this by yourself, you could try the instructions on [http://www.electrictoolbox.com/phpmyadmin-cannot-start-session-without-errors/]("http://www.electrictoolbox.com/phpmyadmin-cannot-start-session-without-errors/") in case clearing the cache wasn't helpful.

Cheers

---

### Post by Brooksy_FC on 2012-03-05
I've tried enabling cookies, but still getting that same error.

---

### Post by baumanno on 2012-03-05
Did you flush the cache, too?

---

### Post by Brooksy_FC on 2012-03-05
No I haven't, how do I do that?

---

### Post by baumanno on 2012-03-05
That depends on your browser:

Chrome/Chromium:
[http://www.technipages.com/google-chrome-clear-cache.html]("http://www.technipages.com/google-chrome-clear-cache.html")

Firefox:
Ctrl+Shift+Del --> Delete all

Or just query Google with "<browser> delete cache"

---

### Post by Brooksy_FC on 2012-03-05
Yep, I've deleted all that, but still the same error :(

---

### Post by baumanno on 2012-03-05
Try the following: [my ouput is the stuff starting with ">>" and need not be typed in]

```

php -i | grep 'Loaded Configuration File'
>> Loaded Configuration File => /etc/php5/cli/php.ini

```

Check contents of that file for **session.save_path**:

```
cat /etc/php5/cli/php.ini | grep session.save_path
```

Obviously, you would change */etc/php5/cli/php.ini* to wherever your loaded php.ini is residing. 

Can you post the output of that last command, please?

---

### Post by Brooksy_FC on 2012-03-05
From the first code I get the same results. 

From the second code I get:

```
ryan@ryan-Latitude-D830:~$ cat /etc/php5/cli/php.ini | grep session.save_path
;     session.save_path = "N;/path"
;     session.save_path = "N;MODE;/path"
;session.save_path = "/tmp"
;       (see session.save_path above), then garbage collection does *not*

```

---

### Post by baumanno on 2012-03-05
What does 
```
cd /
ls -l | grep temp

```

produce? It seems to be a common issue that the permissions aren't sufficient, so writing into the session-dir isn't possible. Check two things please: 

```

cat /etc/php5/cli/php.ini | grep session.save_handler

```
schould be set to "session.save_handler = files" (note that there has to be NO semicolon before this line!), and see whether the permissions listed by the **ls** command (leftmost column of the output) correspond to "drwxrwxrwt" (at least thats what I have here, and my phpMA is working fine...)

---

### Post by Brooksy_FC on 2012-03-05
The first code doesn't seem to work with me. Think I've typed it wrong somewhere...

```
ryan@ryan-Latitude-D830:~$ ls -l | grep temp
ryan@ryan-Latitude-D830:~$ sudo ls -l | grep temp
[sudo] password for ryan: 
ryan@ryan-Latitude-D830:~$ sudo cd ls -l | grep temp
sudo: cd: command not found
ryan@ryan-Latitude-D830:~$ sudo cd/ ls -l | grep temp
sudo: cd/: command not found
ryan@ryan-Latitude-D830:~$ cd / ls -l | grep temp

```

Second code comes back as you said...

```
ryan@ryan-Latitude-D830:~$ cat /etc/php5/cli/php.ini | grep session.save_handler
session.save_handler = files
ryan@ryan-Latitude-D830:~$ 

```

---

### Post by baumanno on 2012-03-05
> **Brooksy_FC said:**
> The first code doesn't seem to work with me. Think I've typed it wrong somewhere...

```
ryan@ryan-Latitude-D830:~$ ls -l | grep temp
ryan@ryan-Latitude-D830:~$ sudo ls -l | grep temp
[sudo] password for ryan: 
ryan@ryan-Latitude-D830:~$ sudo cd ls -l | grep temp
sudo: cd: command not found
ryan@ryan-Latitude-D830:~$ sudo cd/ ls -l | grep temp
sudo: cd/: command not found
ryan@ryan-Latitude-D830:~$ cd / ls -l | grep temp

```

[...]



Sorry, that was my fault, I misspelled "tmp" for "temp", so please do 

```
ls -l | grep tmp
```

---

### Post by Brooksy_FC on 2012-03-05
Ah I see, I've tried

```
sudo ls -l | grep tmp
```

And I get asked to enter my password, I do so and nothing happens

---

### Post by baumanno on 2012-03-05
```
cd /
ls -l | grep tmp

```

---

### Post by Brooksy_FC on 2012-03-05
I get back...

```
ryan@ryan-Latitude-D830:~$ cd /
ryan@ryan-Latitude-D830:/$ ls -l | grep tmp
drwxrwxrwt  13 root root  4096 2012-03-05 14:17 tmp
ryan@ryan-Latitude-D830:/$ 


```

---

### Post by baumanno on 2012-03-05
For the second time today, I'm a bit stumped and did a quick forum search, and this came up:

[http://ubuntuforums.org/showpost.php?p=9814400&postcount=4]("http://ubuntuforums.org/showpost.php?p=9814400&postcount=4")

Open the php.ini in any text editor and delete the semi-colon before the line. Then restart apache by

```
/etc/init.d/apache2 restart
```

---

### Post by Brooksy_FC on 2012-03-05
Ok I'll give that a go. 

I edited the document, tried to over right the old file and it says I don't have the permissions to save the file.

---

### Post by baumanno on 2012-03-05
Try accessing it as root by 
```
sudo gedit /etc/php5/apache2/php.ini
[do some editing]
sudo /etc/init.d/apache2 restart 
```

---

### Post by Brooksy_FC on 2012-03-05
I just the same message to start off with 

> #1045 Cannot log in to MySQL server

---

### Post by baumanno on 2012-03-05
Is mysqld running?

```
ps aux | grep mysqld
```

If yes, can you login from the terminal?

```
mysql -uroot -p
```

If you can, give the root user a new password:

```
mysqladmin -u root password enter_desired_password
```

and then try logging in with the new credentials...

---

### Post by Brooksy_FC on 2012-03-05
I get this from the first code. Is it running?

```
ryan@ryan-Latitude-D830:~$ ps aux | grep mysqld
root      1957  0.0  0.0   4500  1164 ?        S    15:38   0:00 sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking
mysql     1958  0.0  0.4 137468 17688 ?        Sl   15:38   0:00 /usr/sbin/mysqld --skip-grant-tables --skip-networking
mysql     1999  0.0  0.3  93068 13212 ?        Ssl  15:45   0:00 /usr/sbin/mysqld
ryan      2171  0.0  0.0   4192   800 pts/1    S+   15:46   0:00 grep --color=auto mysqld

```


```
ryan@ryan-Latitude-D830:~$ mysql -uroot -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
ryan@ryan-Latitude-D830:~$ 

```

---

### Post by baumanno on 2012-03-05
I can't really see any reason why there should be three instances of mysql running... what does

```
sudo service mysql stop
ps aux | grep mysqld
```

report back?

I'm not familiar with the LAMP-stack, but as far as I know, root has no password on default...?

---

### Post by Brooksy_FC on 2012-03-05
```
ryan@ryan-Latitude-D830:~$ sudo service mysql stop
[sudo] password for ryan: 
mysql stop/waiting
ryan@ryan-Latitude-D830:~$ ps aux | grep mysqld
root      1957  0.0  0.0   4500  1164 ?        S    15:38   0:00 sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking
mysql     1958  0.0  0.4 137468 17688 ?        Sl   15:38   0:00 /usr/sbin/mysqld --skip-grant-tables --skip-networking
ryan      2252  0.0  0.0   4192   796 pts/1    S+   16:02   0:00 grep --color=auto mysqld
ryan@ryan-Latitude-D830:~$ 

```

---

### Post by baumanno on 2012-03-05
That is one hellhound of a mysql-service you have there ;)

I know its not the best practice, but this gets rid of all running instances of mysqld (compare it to a hard shutdown, just with processes):


ONLY DO THIS IF THERE IS NO REASON FOR THE OTHER MYSQLDs TO BE THERE!
```
sudo killall mysqld
```

Then revive it again with

```
sudo service mysql start
```
and try logging in with the aforementioned

```
mysql -uroot -p
```
but no password (just hit enter), unless! you specified one at the installation.

---

### Post by Brooksy_FC on 2012-03-05
Done that.

When I enter no password and press enter I get (using password: NO)

If I try some passwords I get (using password: YES)

no idea what this means, I can't remember the password I used when I set all this up.

---

### Post by baumanno on 2012-03-05
Try 
```
mysqladmin -u root password enter_desired_password
```

again. If it doesn't work, you probably set a password during install. So either rack your brains to figure that out, or go to [these instructions to reset a forgotten mysql-password]("http://www.howtoforge.com/reset-forgotten-mysql-root-password").

Please report back!

Cheers

---

### Post by Tiganjero on 2012-03-05
> **baumanno said:**
> go to [these instructions to reset a forgotten mysql-password]("http://www.howtoforge.com/reset-forgotten-mysql-root-password")

Or use the code from my post [[COLOR="Orange"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11730510&postcount=2"). Don't forget to replace ***newpwd*** with your desired password!

Cheers,
George

---

### Post by baumanno on 2012-03-05
Wasn't seeing the wood for the trees there :popcorn:

---

### Post by Brooksy_FC on 2012-03-06
ryan@ryan-Latitude-D830:~$ mysqladmin -u root password (entered new password)
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I've tried that @Tiganjero, still nothing happens. 

I'll give that other link ago, if not is there a way I can uninstall LAMP and reinstall it, I've got nothing important on the server.

---

### Post by Brooksy_FC on 2012-03-06
Not too worry anymore, I've just done a complete re-install. It's taking too long and I need to get started on this project. I'm gunna stick with a password and won't change it this time.

Thanks for your help guys, if I get any problems, I'll use the comments you suggested.

---

