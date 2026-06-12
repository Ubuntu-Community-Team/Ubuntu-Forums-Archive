---
title: "MySQL"
date: 2012-07-25
forum: General Help
---

### Post by OldManRiver on 2012-07-25
All,

Having a real problem with MYSQL on an Aspire Laptop.  We originally installed Ubuntu with Gnome, but when the WiFi required disable of the "N" mode and still would not maintain stability we switched to KDE ("kubuntu").

WiFi is stable here with no need to disable the "N" mode, but MySQL is another story, always blowing up.  Seems to drop out for almost any reason.

Our latest round we have purged and re-installed serveral time.

The problem seems to be with the client or the server at particular times depending on the message.  No password is accepted regardless of how many times we change it.  Server version is 5.5 (5.5.24) on Kubuntu 12.04 Precice Pangolin.

We've gone through two complete reinstalls, purging, rebooting (making sure all clean is done), re-installing, running dpkg-reconfigure and the safe mode to reset the root password.

Wondering if anyone else has faced this and has some insight, especially on why we are locked out and not able to set the password?

We noticed that the .pid and .perf files, normally in place and holding the passwords and permission are missing.  Wondering if we need to gen blank copies of these files using "touch"?

Some of the errors we are getting are:

> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)




Will appreciate all help given!

Thanks in advance!

OMR

---

### Post by greenpeace on 2012-07-26
Hi!

There's some useful debugging steps on [the wiki]("https://wiki.ubuntu.com/DebuggingMySQL#Debugging_procedure")

Do you have any suspicious entries or clues in the logs?

---

### Post by mastablasta on 2012-07-26
since you are using GUI have you tried to use phpmyadmin to configure mysql database?
also why are you running it as root? note that root database is not the same as root from the OS

---

### Post by OldManRiver on 2012-07-26
> **greenpeace said:**
> Hi!

There's some useful debugging steps on [the wiki]("https://wiki.ubuntu.com/DebuggingMySQL#Debugging_procedure")

Do you have any suspicious entries or clues in the logs?

Greenpeace,

Are you assuming the "apt-get install mysql-server-5.5" is tied to or dependent on the "Apparmor" package?

Thanks!

OMR

---

### Post by OldManRiver on 2012-07-26
> **mastablasta said:**
> since you are using GUI have you tried to use phpmyadmin to configure mysql database?
also why are you running it as root? note that root database is not the same as root from the OS

Mastablasta,

No we were not using any GUIs like phpMyAdmin, as we can not login to mysql in any way shape or form, so we have been relagated to cmd line only, at this point.

GUIs only function when there is a successful login, so no way we can use them.  We have looked at permissions and ownership of the .pid and .sock files but could not find the .perf file.  We feel it is something related to permissions or ownership, as we have followed all the HOWTOs for restoring, creating new and other password HOWTOs, but nothing has worked not even the "dpkg-reconfigure mysql-server-5.5" cmd, which has always worked before.

Purging, Re-installs, Rebuilds have not worked.

It is like the file for the mysql init and passwords is locked and cannot be written to.  Rebooting to clear open files also has not worked.

We have successfully edited the my.cnf file, but changing the user there had no effect on the login.

If you have other ideas of what to do we are open!

Thanks!

OMR

---

### Post by OldManRiver on 2012-07-26
All,

We think this might have been caused by an update package, installing in the background, because it went south all by itself 2 days ago.

Additionally we found the KDE User Admin and all KDE packages with mysql links, had uninstalled themselves and we had to init re-installs on these.

None of the dpkg-reconfigure, mysql, mysqld, or mysql-administrator procesesses will reset the password.

We feel it is something outside of mysql that is locking up the files and not letting the password changes go in.

Your thoughts on this are appreciated!

Thanks!

OMR

---

### Post by sushy on 2012-07-26
Hope you find this link useful. I had tried it myself and it worked for me.

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by greenpeace on 2012-07-27
> **OldManRiver said:**
> Are you assuming the "apt-get install mysql-server-5.5" is tied to or dependent on the "Apparmor" package?

well, I was just hoping to get more information really, and there were some useful links on the page.  

You mention the package mysql-server-5.5, exactly which packages do you have installed?  Did mysql-common and mysql-server-core-5.5 install with it?

This will help you see what's installed: ```
dpkg -l | grep mysql
```

Aside from this, are there any clues in your logs?  I would check: 

**/var/log/mysql/mysql.log** (check that it is enabled in the mysql conf file: /etc/mysql/my.cnf)

**/var/log/syslog**
**/var/log/kern.log**

Do they tell you anything about what's happening?

FYI - I can't find a ".perf" file on my working installation, though I do have a ".pid" file at /var/run/mysqld/mysqld.pid

You say it might be related to a dodgy update.. Do you have a way of checking what was installed / updated over the last few days?  The Ubuntu Software Centre gives me a history of changes, but I don't know if that's available on kubuntu's equivalent (Muon, I think?)

---

### Post by OldManRiver on 2012-07-28
> **sushy said:**
> Hope you find this link useful. I had tried it myself and it worked for me.

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

sushy,

Tried running the helps in the HOWTO link and looked promising, but got the errors of:

ERROR 1133 (42000): Can't find any matching row in the user table 

If I'm understanding this right the user "root@localhost' no longer exists in the user tables, so will have to recreate that user.  Not sure how at this point.

Thanks!

OMR

---

### Post by OldManRiver on 2012-07-28
All the usual logs are suspiciously blank, I hate to wipe and reinstall this machine to solve this problem and still not be able to identify exactly what caused it.  It literally was a night and day kind of thing, one day it was functioning, one day it wasn't.  There may have been an update, there may not have been an update, updates are mostly unattended, but the fact that there's absolutely no trace of what might have happened is cause enough for concern.  If I believe the logs the machine has never done anything at all.

---

### Post by greenpeace on 2012-07-30
> **OldManRiver said:**
> sushy,

Tried running the helps in the HOWTO link and looked promising, but got the errors of:

ERROR 1133 (42000): Can't find any matching row in the user table 

Sounds like a clue!  At which point in the process do you see that error?

---

### Post by OldManRiver on 2012-07-31
root@ndavis-Aspire-7739Z:~# dpkg-reconfigure mysql-server-5.5
mysql stop/waiting
120731 12:55:22 [Warning] Ignoring user change to 'mysql' because the user was set to 'root' earlier on the command line

120731 12:55:22 [Note] Plugin 'FEDERATED' is disabled.
120731 12:55:22 InnoDB: The InnoDB memory heap is disabled
120731 12:55:22 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120731 12:55:22 InnoDB: Compressed tables use zlib 1.2.3.4
120731 12:55:22 InnoDB: Initializing buffer pool, size = 128.0M
120731 12:55:22 InnoDB: Completed initialization of buffer pool
120731 12:55:22 InnoDB: highest supported file format is Barracuda.
120731 12:55:22  InnoDB: Waiting for the background threads to start
120731 12:55:23 InnoDB: 1.1.8 started; log sequence number 368558555
120731 12:55:23  InnoDB: Starting shutdown...
120731 12:55:24  InnoDB: Shutdown completed; log sequence number 368558555
mysql start/running, process 20602
root@ndavis-Aspire-7739Z:~# mysql -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
root@ndavis-Aspire-7739Z:~# 


Above is the output generated when the password is supposedly reset.  Someone mentioned that it could be AppArmor that is causing this, if possible could anyone post more details on that, please and thank you.

---

### Post by greenpeace on 2012-08-01
> **OldManRiver said:**
> ```
dpkg-reconfigure mysql-server-5.5
```

Did you follow all the steps on the community page indicated by another poster? [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

what happens when you run MySQL with the **--skip-grant-tables** flag?  Are you able to access the server in that way?

How are you starting the server, and can you show the startup script? it's here on my box: **/etc/init/mysql.conf**

Also, can you post the contents of your my.conf? (**/etc/mysql/my.cnf**)

---

### Post by OldManRiver on 2012-08-01
Greenpeace,

We run the one error doing the following:
[LIST]
[*]dpkg-reconfigure mysql-server_5.5,
[*]reset the password,
[*]mysql restarts itself,
[*]execute "mysql -u root -p",
[*]enter the password.
Gets error:
> ERROR 1133 (42000): Can't find any matching row in the user table.
[/LIST]
The other error comes frmo following the steps of the HOWTO at:
> [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
Steps of (in sudo):
[LIST]
[*]/etc/init.d/mysql stop,
[*]/usr/sbin/mysqld --skip-grant-tables --skip-networking &,
[*]mysql -u root,
[*]FLUSH PRIVILEGES;,
[*]SET PASSWORD FOR root@'localhost' = PASSWORD('password');,
[*]UPDATE mysql.user SET Password=PASSWORD('newpwd') WHERE User='root';,
[*]FLUSH PRIVILEGES;,
[*]/etc/init.d/mysql restart.
[*]mysql -u root -p,
[/LIST]
Gets error:
> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
Have also done the alternates of:
[LIST]
[*]/etc/init.d/mysql stop,
[*]/usr/sbin/mysqld --skip-grant-tables --skip-networking &,
[*]mysql -u root,
[*]FLUSH PRIVILEGES;,
[*]USE mysql;,
[*]UPDATE user SET Password = PASSWORD('newpwd') WHERE Host = 'localhost' 
					AND User = 'root';,
[*]UPDATE user SET Password = PASSWORD('newpwd') WHERE Host = '%' 
					AND User = 'root';,
[*]FLUSH PRIVILEGES;,
[*]/etc/init.d/mysql restart.
[/LIST]
These are getting errors of:
> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

so password just set is not taking.  We manually deleted the "mysql" DB and dir and then re-installed to rebuild it, but no change in the results.

So I logged into mysql in this safe mode, being used, went to the mysql DB, ran a "Select * From user;" and got the following:

mysql> select * from user;
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+------------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+--------+-----------------------+
| Host      | User             | Password                                  | Select_priv | Insert_priv | Update_priv | Delete_priv | Create_priv | Drop_priv | Reload_priv | Shutdown_priv | Process_priv | File_priv | Grant_priv | References_priv | Index_priv | Alter_priv | Show_db_priv | Super_priv | Create_tmp_table_priv | Lock_tables_priv | Execute_priv | Repl_slave_priv | Repl_client_priv | Create_view_priv | Show_view_priv | Create_routine_priv | Alter_routine_priv | Create_user_priv | Event_priv | Trigger_priv | Create_tablespace_priv | ssl_type | ssl_cipher | x509_issuer | x509_subject | max_questions | max_updates | max_connections | max_user_connections | plugin | authentication_string |
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+------------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+--------+-----------------------+
| localhost | debian-sys-maint | *FDB2C38E187882D7804CF3BCC79D2963E00AF20F | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            | N                      |          |            |             |              |             0 |           0 |               0 |                    0 |        | NULL                  |
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+------------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+--------+-----------------------+
1 row in set (0.00 sec)

which shows what I thought, there is no "root" user, so created using:

INSERT INTO user (Host, User, Password, Select_priv, Insert_priv, Update_priv, Delete_priv, Create_priv, Drop_priv, Reload_priv, Shutdown_priv, Process_priv, File_priv, Grant_priv, References_priv, Index_priv, Alter_priv, Show_db_priv, Super_priv, Create_tmp_table_priv, Lock_tables_priv, Execute_priv, Repl_slave_priv, Repl_client_priv, Create_view_priv, Show_view_priv, Create_routine_priv, Alter_routine_priv, Create_user_priv, Event_priv, Trigger_priv, Create_tablespace_priv, ssl_type, ssl_cipher, x509_issuer, x509_subject, max_questions, max_updates, max_connections, max_user_connections, plugin, authentication_string) VALUES 
	('localhost', 'root', 'newpass, 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', '', '', '', '', 0, 0, 0, 0, '', NULL),
	('%', 'root', 'newpass', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', '', '', '', '', 0, 0, 0, 0, '', NULL);

Then went out of mysql safemode and ran the "mysql -u root -p"  entered my password and finally it is working!

What is bothering me though is the system is holding something that is keeping the "root" user from being regenerated when we deleted the DB, it's dir, purged the package, rebooted and then re-installed.

The root user should have come up automatically, so hoping someone out there know what is the system is holding this out.

Thanks all!

OMR

---

### Post by OldManRiver on 2012-08-06
All,

When I posted last was trying to find out why the system was keeping a new install from rebuilding with the "root" user.

Does anyone have any ideas, what might be causing this?

OMR

---

### Post by SeijiSensei on 2012-08-06
Have you tried "sudo apt-get purge mysql-server" and then deleting /var/lib/mysql with "sudo rm -rf /var/lib/mysql"?  

Usually when you install mysql-server on a fresh machine you'll be asked to specify the root password during the installation.  A text-mode screen will pop up along the way asking for the root password.

I suggested deleting /var/lib/mysql in case a new installation tries to use the existing database structure it finds there.

---

### Post by OldManRiver on 2012-08-16
> **SeijiSensei said:**
> Have you tried "sudo apt-get purge mysql-server" and then deleting /var/lib/mysql with "sudo rm -rf /var/lib/mysql"?  

Usually when you install mysql-server on a fresh machine you'll be asked to specify the root password during the installation.  A text-mode screen will pop up along the way asking for the root password.

I suggested deleting /var/lib/mysql in case a new installation tries to use the existing database structure it finds there.

SeijiSensei,

Oh yeah, did that mulitple times, and what you describe is what normally happens, so was really blown out when this did not work.  At least it is working now and we know how to restore, in the future, but sure was a pain and the fact that something in the system kept forcing it to not build out the "root" user, was the most puzzling.

We still do not have an answer for that, but wondering if I should close this thread anyway.  Not sure if we will ever know this answer.

Cheers!

OMR

---

### Post by mastablasta on 2012-08-16
well i couldn't reset the password either. i never did work with system root acocunt. i used user accout with elevated privileges. there are 2 roots. one is system and one is MySql. they are different. So by not working with root account i did know that the server one was giving me the issue. 
 
and you said you are using KDE which is a GUI and this is what i've ment before. so you could just install phpmyadmin to it and use the browser to access it. then change the password there. i did it like that and it worked. and i still don't know why it didn't work with commands.

---

### Post by OldManRiver on 2012-10-10
> **mastablasta said:**
> well i couldn't reset the password either. i never did work with system root acocunt. i used user accout with elevated privileges. there are 2 roots. one is system and one is MySql. they are different. So by not working with root account i did know that the server one was giving me the issue. 
 
and you said you are using KDE which is a GUI and this is what i've ment before. so you could just install phpmyadmin to it and use the browser to access it. then change the password there. i did it like that and it worked. and i still don't know why it didn't work with commands.

mastablasta,

No phpMyAdmin did not and is not working if you can not login via command line, and especially without any users. phpMyAdmin likes to install it's own phpMyAdmin user with "ALL" or root privileges, I of course recreated all the 6+ users I normally have, after getting in so now phpMyAdmin now works.

But thanks for the think thru.

Closing this thread.

Cheers!

OMR

---

