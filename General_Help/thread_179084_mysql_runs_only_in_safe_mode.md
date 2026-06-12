---
title: "mysql runs only in safe mode"
date: 2006-05-19
forum: General Help
---

### Post by cromestant on 2006-05-19
I've been searching on the net, reading the info and man pages... but can't seem to fix this issue

my mysql only runs in safe mode, and therefore doesn't let me get external conections...
I don't know why, when i do a restart or start i ge this :
root@Bob:/var/cache/apt/archives# /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
FIXME: This is still too noisy but will be changed, soon!
root@Bob:/var/cache/apt/archives# This script updates all the mysql privilege tables to be usable by
MySQL 4.0 and above.

This is needed if you want to use the new GRANT functions,
CREATE AGGREGATE FUNCTION, stored procedures, or
more secure passwords in 4.1

Got a failure from command:
cat /usr/share/mysql/mysql_fix_privilege_tables.sql | /usr/bin/mysql --no-defaults --force --user=root --host=localhost --database=mysql
Please check the above output and try again.

Running the script with the --verbose option may give you some information
of what went wrong.

If you get an 'Access denied' error, you should run this script again and
give the MySQL root user password as an argument with the --password= option
Checking for crashed MySQL tables in the background.


I tried running the command, and it says there are a lot of duplicate column names, so searching the net, i found that a flush privileges fixes this, but no..

Now I was able to backup my tables, and did
aptiture purge mysql-server-5.0
then emptied the /var/run/mysql folder
and the /etc/mysql/ folder
(also deleted the folders)

then I deleted the aptitude packages, so that I really get  a new install
(/var/cache/apt/archives)
then did 
aptitude install mysql-server-5.0
it redownloaded the packages redid the install 

redid the config for the root user, then tried to start it up, and nothing.. same error

put my backup back in in safe mode ( so it works on localhost and phpmyadmin). but still i only get the safe mode..
I really need this to work ,since i am doing a project for the university in j2ee, and cvs, so my companions need to be able to test the development by accesing my db remotely..

any help would be apreciated.

Thank you

sorry for the long post](*,)

BTW my my.cnf has the bind address set to 127.0.0.1, I don't know if its true  but I think that this might be the cause... 
if it is, can you please tell me what I can put there for it to listen to all conections?

Ok I read up a little more and yes the bind address binds the socket to only listen to localhost, so in theory this should work, but I stillonly have safe mode..

---

### Post by cromestant on 2006-05-20
Kindof fixed itself on reboot, although I was right, the bind=address 127.0.0.1 does bind the listening to the loopback interface, and ONLY to it... so no posble conections from outside.

Just commend out that line and restart it ( or your pc in mi case)

anyway the best way to secure your server is not by doing this, but instead by using a good firewall and properly configured iptables

---

