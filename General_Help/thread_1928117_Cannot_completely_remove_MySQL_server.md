---
title: "Cannot completely remove MySQL server"
date: 2012-02-19
forum: General Help
---

### Post by HunterT on 2012-02-19
Hello, I'm running Ubuntu 10.10 on a Dedicated machine. 
I have followed many guides like: 
[http://stuffthatspins.com/2011/01/08/ubuntu-10-x-completely-remove-and-clean-mysql-installation/](http://stuffthatspins.com/2011/01/08/ubuntu-10-x-completely-remove-and-clean-mysql-installation/)
and one other on this forum, but still, I have no luck!

My hard drive is not full!
When I completely remove MySQL from the guide, it is still partially on because I don't know the root password. I tried the sqladmin blah blah password command, but it couldnt connect to the mysql server because of a socket problem or something?

I'm willing to pay for somebody to help me step by step to completely remove/install MySQL server. Thanks in advanced

---

### Post by Leppie on 2012-02-19
which root password do you not have? the system one, or the mysql one?

---

### Post by HunterT on 2012-02-19
> **Leppie said:**
> which root password do you not have? the system one, or the mysql one?
Both.
My my user1 account for the system can do anything.

---

### Post by TheFu on 2012-02-19
If you follow that guide, just put 'sudo' before each of the commands they recommend.
OR
type 'sudo -s' before you get started.

You don't need to know the mysql root password, you just need to have root system access - on Ubuntu-based distros, that elevation comes thru 'sudo'

---

### Post by HunterT on 2012-02-19
> **TheFu said:**
> If you follow that guide, just put 'sudo' before each of the commands they recommend.
OR
type 'sudo -s' before you get started.

You don't need to know the mysql root password, you just need to have root system access - on Ubuntu-based distros, that elevation comes thru 'sudo'
I did! I did all of that! Except once it came time to remove the last bit of MySQL it would ask me for the MySQL root password, which I don't know. Then I would have to ignore/abort and then mySQL would still be running :/

This is what I get after I follow that whole Guide (installing mysql-client):
> invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up mysql-client (5.1.58-1ubuntu1) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because MaxReports is reached already
                                                              ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Here is the MySQL status:
> user1@clf-110:~$ service mysql status
mysql stop/waiting
This is what I get when I try to change the password:
> 
user1@clf-110:~$ mysqladmin -u root -p status
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
user1@clf-110:~$ mysqladmin -u root -p status
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!




---

### Post by TheFu on 2012-02-19
Try 
$ sudo /etc/init.d/mysql stop

first.  Sorry, I never used 10.10, but I have used 8.04 and 10.04 extensively.

For the purge commands, I'd use:
$ sudo -s
# apt-get purge mysql*

If you have any php?-mysql, you may want to remove that first, but the automatic dependencies resolver should handle that for you.

If it fails next time, please copy/paste the exact command AND all the output here to get better help.

---

### Post by Leppie on 2012-02-19
I believe that the initial mysql root password is blank, so if you have never set the password for the mysql root account try the following:
```
# mysql -u root
```However, it looks like mysql is no longer running on your machine:
```
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

---

### Post by HunterT on 2012-02-19
> **Leppie said:**
> I believe that the initial mysql root password is blank, so if you have never set the password for the mysql root account try the following:
```
# mysql -u root
```However, it looks like mysql is no longer running on your machine:
```
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```
Okay I was able to Completely purge mySQL. So now I followed a new tutorial to get it all back: [https://help.ubuntu.com/11.04/serverguide/C/mysql.html](https://help.ubuntu.com/11.04/serverguide/C/mysql.html)
So it asks me to set an administrator password, so I set it.
Then I get phpmyadmin , and when it asks the for SQL administrative password.. It says 
"error: 'Access denied for user 'root'@'localhost' (using password: YES)'" ... This is really starting to annoy me! Help?

---

### Post by TheFu on 2012-02-20
If mysql is removed and purged, why should phpmyadmin work?
I'd purge that tool as well.

---

### Post by HunterT on 2012-02-20
> **TheFu said:**
> If mysql is removed and purged, why should phpmyadmin work?
I'd purge that tool as well.
No, I purged it then I got a new copy! This is three days my SQL server isn't working :(.
Do you have teamviewer or skype?

---

