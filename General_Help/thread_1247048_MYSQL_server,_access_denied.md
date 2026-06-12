---
title: "MYSQL server, access denied"
date: 2009-08-22
forum: General Help
---

### Post by Weidbrewer on 2009-08-22
I'm trying to get my SQL server set up on my 8.10 64-bit install, but keep hitting a wall.  Thinking that I must have screwed something up, I uninstalled and attempted to start over.  The installation instructions that I find out there are all the same - and I always hit the same problem:

```
sudo apt-get install mysql-server

```

The above works fine.  Then, instructions say to start it:

```
sudo /etc/init.d/mysql start
```

...and then set the password:

```
mysqladmin -u root password MYPASSWORD
```

(And, just to eliminate the obvious, I did *not* set my password to "MYPASSWORD" :) )

When I do the above, I get this result:
```
*****@******:~$ mysqladmin -u root password mythtv
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```


What am I doing wrong?

---

### Post by DaithiF on 2009-08-22
Sounds like a password has already been set for the root user.
If you remember what it is, then try to login:
mysql -u root -p<password>
(no space between the -p and your password).

---

### Post by Weidbrewer on 2009-08-22
Well, there-in would be the problem.  As you can see from the above steps, I only set a password as part of the install.  (Those steps are a cut and paste as I did them.)  

Unless:

[LIST]
[*]The root password is the same as my system root password. (login, sudo, etc)
[*]Or it's remembering something from a previous install that didn't get removed with sudo apt-get remove.
[/LIST]

If the first one, how does that work?  If the second one, how do I fully remove everything and start over?

---

### Post by DaithiF on 2009-08-23
Hi, 
mostly likely the second of those.
So the steps to follow will be:
1. stop mysql
2. start it again in a special mode which doesn't require permissions
3. connect and change the root password
4. stop the server & restart it in normal mode

1. stop mysql
```
  sudo /etc/init.d/mysql stop

```2. start it again in a special mode which doesn't require permissions
 ```
/usr/bin/mysqld_safe --skip-grant-tables &

```3. connect and change the root password
  ```
mysql -u root 

```then at the mysql prompt
change to the mysql system database and change the password
```
use mysql;
update user set password = PASSWORD('yourpasswordhere');
flush privileges;

```

4. stop the server & restart it in normal mode
```
sudo /etc/init.d/mysqld stop
sudo /etc/init.d/mysqld restart

```

---

### Post by DaithiF on 2009-08-23
forgot to mention, at the end of step 3, you'll need to exit from mysql to get back to your terminal prompt.  so after flush privileges;, do
```
exit
```

---

### Post by Weidbrewer on 2009-08-28
**DaithiF** - Thank you for taking the time to respond.  I haven't been ignoring you...this week just really got away from me.  This DB is on the 64-bit partition of my media server (trying to migrate) and the only times I've had to work on it this week, it's been in use.

I really hope to get to it tomorrow after my fantasy football draft, but it's summer and there's yard work...  grr.

---

### Post by Weidbrewer on 2009-08-29
Okay...I still got nothing.  The following are the results of the big fat nothing I've been able to accomplish (can't get past step 2.)  If there is something glaringly obvious that only a moron would miss, please assume that I am an utter and total moron:

```
****@****:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                 [ OK ]
****@****:~$ /usr/bin/mysqld_safe --skip-grant-tables &
[1] 9281
****@****:~$ nohup: ignoring input and redirecting stderr to stdout
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[9320]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[9334]: ended

```

That's it.  Nothing happens from there.  For a laugh, I just typed your next command, even though there was no prompt:

```
mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[1]+  Done                    /usr/bin/mysqld_safe --skip-grant-tables
****@****:~$
```


Any suggestions?

---

### Post by wojox on 2009-08-29
Try this:

```
mysql -u root -p mysql
```

---

### Post by DaithiF on 2009-08-29
yep, my bad, sorry ... prefix the command in #2 with sudo :)
mysqld_safe is starting up, and trying to access its databases in /var/lib/mysql but since its running as your user id, it doesn't have the required privileges and so it exits again more or less immediately.

---

### Post by Weidbrewer on 2009-08-29
Oh man...this just ain't my day... :lolflag:  I wasn't expecting a response that fast...much les *two* responses, so I totally nuked it and am reinstalling...but, if I end up back at ground zero again, I will run through the above again.  (I need to learn to leave well-enough alone...)

---

### Post by Weidbrewer on 2009-08-29
Well, reinstalling and setting it up seemed to 
A.) "Solve" my problem and 
B.) Show me that the problem I had is not the problem I thought I had.

I can log in to MySQL just fine now, as is evidenced:

```
***@***:~$ mysql -u root -p mysql
Enter password:
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

```

Where I run in to troubles is when I'm trying to use it.  I'm attempting to set up MythTV on this partition (used heavily on my 32-bit partition)  However, when I start it up, it can't find the backend because (I suspect) that it cannot find the DB.  This makes sense, since I doubt it is there.  I need to create:

[LIST=1]
[*]A MySQL MythTV user named "mythtv," with a password (with will be the same as the root one.)
[*]A MySQL MythTV database called "mythtv"
[*]On my MySQL server, we'll call it, "Bob."
[/LIST]

This is because my mysql.txt in /etc/mythtv points to:

DBUserName=mythtv
DBPassword=*****
DBName=mythtv
DBType=QMYSQL3

This mirrors what is set up on the working partition.  Therefore, I attempted to set up the DB by both of the following methods with the following results:

```
mysql> CREATE DATABASE mythtv
    ->
```

Tried this both uppercase and lower case, with the same results - it just gives me that blank line below it.

I also attempted:
```
****@****:~$ mysqladmin -u root -p create mythtv
Enter password:
mysqladmin: CREATE DATABASE failed; error: 'Can't create database 'mythtv'; database exists'

```

So, apparently, it exists...somewhere.  I just don't know where, or how to access it.

So, there's my layout.  The problem is now much different than my original, and I should probably have started a new thread...but I've got you guys watching this one, so I'll give it a whack.

I promise that I'll keep my hands off until I hear back so that I don't progress any farther in to a big pile of poo while I wait.

---

### Post by unutbu on 2009-08-29
Put a semicolon after every mysql command:
```

CREATE DATABASE mythtv;


```
Edit: The other command shows you already have a mythtv database, so the above is unnecessary.

Read this to see the command for how to add new users:
[http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)

---

### Post by Weidbrewer on 2009-08-29
```
mysql> CREATE USER 'mythtv'@'localhost' IDENTIFIED BY '**<PASSWORD_HERE?>**';
ERROR 1396 (HY000): Operation CREATE USER failed for 'mythtv'@'localhost'
mysql> 

```

Those steps look like some other that I have done, however when I check for privileges granted to that user:

```
mysql> SHOW GRANTS FOR 'mythtv'@localhost';
    '> 

``` 

...I get nothing.

---

### Post by unutbu on 2009-08-29
> CREATE USER 'mythtv'@'localhost' IDENTIFIED BY '<PASSWORD_HERE?>';


Did you substitute your mysql mythtv password  in place of  <PASSWORD_HERE?> ?  Other than that, the syntax looks correct to me.


> 
mysql> SHOW GRANTS FOR 'mythtv'@localhost';
    '>

You're missing a single-quote before localhost:
```

SHOW GRANTS FOR 'mythtv'@[COLOR="Red"]'[/COLOR]localhost';
```

---

### Post by Weidbrewer on 2009-08-29
> **unutbu said:**
> Did you substitute your mysql mythtv password  in place of  <PASSWORD_HERE?> ? 

That I did...just making sure that was where it was supposed to be.


> 
You're missing a single-quote before localhost:
```

SHOW GRANTS FOR 'mythtv'@[COLOR="Red"]'[/COLOR]localhost';
```

Okay, I can change that - thanks for pointing it out...Next question:  How do I find that DB, and more importantly, how do I get MythTV to find that.

---

### Post by Weidbrewer on 2009-08-30
Okay...two steps forward, two steps back.  (If anyone sings Paula Abdul, I will not be pleased.)

First off, when I booted in to this partition just now, everything that I had done yesterday seemed to be gone, because I couldn't log in to MySQL any longer.  So, I did **DaithiF**'s instructions from a page back and was able to get in (Though, it didn't seem to like the start/stop commands for some reason...they errored out.)

Once in, I checked the database (still says it's already created) and the permissions for user MythTV:

```
mysql> CREATE DATABASE mythtv;
ERROR 1007 (HY000): Can't create database 'mythtv'; database exists
mysql> CREATE USER 'mythtv'@'localhost' IDENTIFIED BY '<pasoword>';
ERROR 1396 (HY000): Operation CREATE USER failed for 'mythtv'@'localhost'
mysql> SHOW GRANTS FOR 'mythtv'@'localhost';
+------------------------------------------------------------------------------------------------------------------------------------------+
| Grants for mythtv@localhost                                                                                                              |
+------------------------------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'mythtv'@'localhost' IDENTIFIED BY PASSWORD '<Long string of characters here>' WITH GRANT OPTION | 
| GRANT ALL PRIVILEGES ON `mythconverg`.* TO 'mythtv'@'localhost'                                                                          | 
+------------------------------------------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)

```

Now, what is interesting here is that it's saying the permissions are there for mythconverg, which is the default MythTV DB name - now mythtv, which is the name of the DB I created (and can't find.)


Note:  **unutbu** - yes, I have my actual password there, not <password>

---

### Post by unutbu on 2009-08-30
To list the available databases, you could run
```

mysql> show databases;
```

---

### Post by Weidbrewer on 2009-08-30
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mydababase         | 
| mysql              | 
| mythconverg        | 
| mythtv             | 
| tempattempt        | 
+--------------------+
6 rows in set (0.00 sec)

```

Here is the list of what I found...Which still leaves me with the problem of not knowing where they are, or how to get mythtv to access them.  They do not seem to be in my mysql or mythtv folders.

EDIT (Part II): In the MythTV general settings, I changed the server name to "local host" and now it can access the DB.  I can't seem to get the remote frontends to connect to it, however.  When I check the control center and click the "Test MySQL Connection button, I get a failure.  All of the info (user, password, server) are all correct, so I'm not sure.

that's probably a question for the MythTV forums, though.  Pretty much all this leaves me with here is finding out where the physical DB file is.

---

### Post by unutbu on 2009-08-30
The database files are in /var/lib/mysql. 

If you say
```

mysql> use mythtv;
mysql> show tables;
```

You'll see the tables inside the mythtv database.

If one of the tables is named 'metadata' for instance -- you can tell I know nothing about MythTV -- then you can say
```

mysql> describe metadata;
```

to see the fields of the table, and you can say
```

mysql> select * from metadata limit 10; 
```

to see the first 10 records in the metadata table.

I'm not sure if this is helpful or not. Hope so. Is it? :confused:

---

### Post by DaithiF on 2009-08-30
Hi,
just to summarise -- it seems like you have the databases you need setup, and you have the required mythtv user created & given it the required privileges, right?  So the last problem is that your mythtv isn't find the database?  

is mysql running on the same server as mythtv?  If yes, then as long as you've configured mythtv with the correct db username and password then there shouldn't be anything else required.  If mythtv is on a different computer, then you will have some additional steps to do.

---

### Post by Weidbrewer on 2009-08-30
**unutbu** - I found the folders where you said they were, so that worked out.  I realized that what I was looking for was a text file version of that...but now I remember that I got that through a back-up utility and is only needed for a certain set of situations...bottom line - I think I've got what I need as far as that goes now.  Thanks!


**DaithiF** - On the master backend/frontend, things now seem to be working as they should.  Mission accomplished there.  However, I have three remote frontends that had all been working fine on the old system that are not able to connect now.  All of them had been set up with an ip address (192.168.1.47) instead of a server name, and that had been working.  The IP address has not changed at all, nor has the user name/password information.

Additionally, I was looking at the mysql.txt of the old (working) partition (I have it in a backup folder on this side, and the entire file consisted of:

```

DBHostName=<host name here>
DBUserName=mythtv
DBName=mythtv
DBPassword=<password here>
```


The one on this partition is:

```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBUserName=mythtv
DBPassword=<passowrd here>
DBName=mythtv
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for is....etc, etc, etc....
```

I realize that the majority of that is just commented out info, but for giggles, I created a back-up of this partition's file and then edited it to be the same as the other...still no luck.

So, summary:
Masterbackend: groovy
Remote frontends:  No settings changed, but they cannot connect.



(I appreciated everyone's help, BTW.)

---

### Post by DaithiF on 2009-08-30
Ok, good.  For the remote frontends, theres likely 2 things you'll need to check/change
1. mysql may not be listening on the network for connections (by default a new install DOES NOT listen on the network, only on the local host).  Therefore any connection attempts from remote frontends will fail.
To tell mysql to listen on the network, edit /etc/mysql/my.cnf, find the line  bind-address  = 127.0.0.1 and comment it out by prepending the line with a # character
you'll then need to restart mysql:
```
sudo /etc/init.d/mysql restart

```
2. the mythtv username that the frontends will be connecting from will be connecting from their hosts, rather than from localhost.  So the mythtv@localhost user that you set up won't be enough to grant them access.  You could add entries for specific IPs, ie. [email]mythtv@xx.xx.xx.xx[/email], or specific hostnames, or you can use the blanket mythtv@'%' wildcard to match any servers.  So decide which you want, create the required user entries like you did before, grant them the same privileges, and again restart the mysql server.

fingers crossed.

---

### Post by Weidbrewer on 2009-08-30
Hmmm...the second one is one that I definitely didn't have to do before (like I said, I haven't touched the login information on the frontends - they're still set to what they were, and it was a working configuration.)  The first one seems vaguely familiar, so I will give that a whirl and see what happens from there.  After that, I'll move on to step two if need be.  

Thanks for the input.

---

### Post by DaithiF on 2009-08-31
Hi,
I think maybe you've misunderstood what I was trying to say in #2.  Its not about changing the details that the frontends log in with, those details can stay the same.  Its about telling the server that its ok for mythtv@<some computer other than this one> to log in.  If your only mythtv login on the server is mythtv@localhost then the only login attempts for mythtv that will succeed are those that come from localhost.  If you add mythtv@'%' then mythtv connections from *any* computers will be allowed.

---

### Post by Weidbrewer on 2009-08-31
Yep...that's exactly what happened. (Misunderstanding, that is.)  I didn't get a chance to do step one last night anyway, so I will try to get to that after work.

Sweet Jesus...my idiocy here has bumped my posts up to the next level of beans.  That's not right...

---

### Post by Weidbrewer on 2009-08-31
Attention Ubuntuians:

**DaithiF** rocks the Casbah.  

That is all.

---

### Post by Weidbrewer on 2009-09-04
Looks like I need to reopen this.  For unrelated reasons, I needed to reboot the backend, and it seems to have reverted everything.  (At least it can't find the Myth backend any longer, and the MySQL DB is locked back up.  Didn't have time to muck with it farther than that.)

Assuming I can just retrace the above steps to get back in business, what do I need to do to not have it overwrite it again?

---

### Post by DaithiF on 2009-09-06
Hi,
a reboot shouldn't have affected any of these settings.  only thing i can think of is if your mysql server isn't configured to start on boot.

can you check first if mysql is running on your mythtv server:
```
sudo /etc/init.d/mysql status 

```
Note that trying to log in to a server that is not running will give an error message like 'access denied', which doesn't make it very obvious that the server just needs to be started.

To configure your system so that mysql starts on boot, do:
```
sudo update-rc.d mysql defaults 

```
good luck

---

### Post by Weidbrewer on 2009-09-06
Thanks...it was not running, and when I tried to start it, it gave me an error stating that the partition was full...this connected to an issue that I had last week where a download directory had been set incorrectly, and I forgot to delete everything out of there...once I did that and rebooted, smooth sailing again.

---

### Post by ktritty on 2009-09-10
Hello.  I have a similar problem, almost the exact in fact.  I cannot get anything mysql to work.  I am trying to work my way through the steps.

> **DaithiF said:**
> 
1. stop mysql
2. start it again in a special mode which doesn't require permissions
3. connect and change the root password
4. stop the server & restart it in normal mode

[/code]4. stop the server & restart it in normal mode
```
sudo /etc/init.d/mysqld stop
sudo /etc/init.d/mysqld restart

```

The first 3 steps went great.  

My problem is step 4.  I try to type the stop command (I have tried sudo /etc/init.d/mysql stop AND sudo /etc/init.d/mysqld stop).  The former gives [fail] and the latter gives command not found.

Advice??

---

### Post by DaithiF on 2009-09-10
sorry, the command should be sudo /etc/init.d/mysql stop, not mysqld as i had put in the previous post.  can you post the full message you get when you issue the stop command.
thanks

---

### Post by ktritty on 2009-09-11
I tried to restart the system using $sudo shutdown -r now.  The mysql failed to kill, the system tried twice.  Upon restart, the following message displayed:
```

* Checking for corrupt, not cleanly closed and upgrade needing tables.
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)

```I am stuck.  I also don't know how to try to uninstall/reinstall mysql.  I have tried several aptitde commands, but whatever bug I have still remains.  I run ```
$aptitude search mysql > mysql.txt
``` and I get the output in the attachment.

Ideas?

---

### Post by ktritty on 2009-09-13
Update:

After lots of arm-wrestling with my armless server, I was able to finally get mysql fully deinstalled using a frustratingly long series of commands in aptitude and apt-get, to hopefully minimize doing any damage.

I then reinstalled:
$ sudo apt-get install mysql-server-5.0

which then ran and all was rosy until:
* Starting MySQL database server mysqld
invoke-rc.d: initscriptmysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1

Now, when I try:
$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld             [fail]

Is there a way to somehow catch an exit code and figure out what on earth is going on?  I would really like to avoid a full reformat of the hard drive at all costs, I've got other things going on on this server.  So, any help in understanding what part of the /etc/init.d/mysql is failing would be awesome!

---

### Post by unutbu on 2009-09-13
ktritty, I notice this error in your previous post:
```

'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)
```

debian-sys-maint is a special user that mysql sets up at the time that the
mysql-server-5.0 package is installed. 

The mysql user/host/passwords -- including the one for debian-sys-maint -- are stored in the directory
/var/lib/mysql/mysql.

I you happened to copy /var/lib/mysql/mysql from a previous installation, and then tried to install the mysql-server-5.0 package, then I think you might end up having problems (and the exact error you posted above) because the password for debian-sys-maint listed in /etc/mysql/debian.cnf may not match the password in the /var/lib/mysql/mysql database.

Does this sound like your situation?

If so, I suggest you 
[list]
[*] backup any personal databases in /var/lib/mysql,
[*]purge the mysql-server-5.0 package, 
```
sudo apt-get purge mysql-server-5.0
```
[*]delete the /var/lib/mysql directory, and 
[*]reinstall mysql-server-5.0:
```
sudo apt-get install mysql-server
```
[/list]

---

