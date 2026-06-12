---
title: "Sympa Error?"
date: 2012-02-17
forum: General Help
---

### Post by Draygo81 on 2012-02-17
howdy all, 
I did a forum search sympa error, sympa, and got back nothing.

I am currently running ubuntu 11.10 on my HP Netbook, and wasnt having any issues until a friend recommended cairo-dock. I downloaded and installed it and then attempted to remove it. in the terminal window i get a sympa error. I am fairly new to ubuntu, but reeealy like it. oh, and is there a netbook friendly ubuntu out there? i couldn't find the ubuntu-remix... :\

Thanks for any help. 

Amy

---

### Post by cwklinuxguy on 2012-02-17
Can you please post the error message that the terminal gives you?

Ubuntu Netbook Remix was officially continued as of the 11.04 release when Unity fully took over as the interface for ALL devices running Ubuntu. I imagine that you can still find old installation CDs and/or ISOs if you look around, however I've never found these Netbook interfaces to be of much use. To me, a Netbook is no different than any other laptop: it's just got a smaller screen size, so I find the idea of putting a less useful UI on it to be rather useless--I find that normal desktop interfaces usually work fine, and are even better and more flexible than 'netbook' UIs. However, my short-lived experience of trying to run Unity on a netbook didn't go very well. You may want to experiment with using other desktop environments.

---

### Post by Draygo81 on 2012-02-17
I just did a apt-get autoremove to recreate the sympa error, but its the same one everything...


~$ sudo apt-get autoremove
[sudo] password for [user]: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up sympa (6.1.1~dfsg-2) ...
dbconfig-common: writing config to /etc/dbconfig-common/sympa.conf
Not configuring Web server.
DBI connect('sympa:localhost','user_name',...) failed: Access denied for user 'user_name'@'localhost' (using password: YES) at /usr/share/sympa/lib/SQLSource.pm line 173
err SQLSource::connect() Can't connect to Database DBI:mysql:sympa:localhost as user_name
err List::check_db_connect() Failed to connect to database
DBI connect('dbname=mysql;host=localhost','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at /usr/share/sympa/lib/SQLSource.pm line 313
err SQLSource::create_db() Cannot connect as root to database
Database sympa defined in sympa.conf has not the right structure or is unreachable. verify db_xxx parameters in sympa.conf
dpkg: error processing sympa (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 sympa
E: Sub-process /usr/bin/dpkg returned an error code (1)
~$ 

hopefully someone can read thru the codes... 
Thanks again

---

### Post by novicecoder on 2012-02-19
I am also having this exact problem, with it happening anytime I try updating or installing something. As my username shows, I'm kind of new to this, and help would be appreciated.
--------------------------------------------------
Terminal output: 

[B][COLOR="Navy"]user@user-LatD610:~$  sudo apt-get install libimobiledevice-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libimobiledevice-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  sdparm libhal1 hal libhal-storage1 hal-info
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up sympa (6.1.4~dfsg-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/sympa.conf
apache2: installation seems OK ...
apache2: installation seems OK ...
No apache MPM package installed
DBI connect('sympa:localhost','user_name',...) failed: Access denied for user 'user_name'@'localhost' (using password: YES) at /usr/share/sympa/lib/SQLSource.pm line 173
Please install an MTA on this system if you want to use sendmail!
err mail::sending() could not close safefork to sendmail
err List::send_global_file() List::send_global_file, could not send template /usr/share/sympa/default/mail_tt2/listmaster_notification.tt2 to listmaster@user-LatD610
err SQLSource::connect() Unable to send notify 'no_db' to listmaster
err SQLSource::connect() Can't connect to Database DBI:mysql:sympa:localhost as user_name
err List::check_db_connect() Failed to connect to database
DBI connect('dbname=mysql;host=localhost','root',...) failed: Access denied for user 'root'@'localhost' (using password: NO) at /usr/share/sympa/lib/SQLSource.pm line 313
err SQLSource::create_db() Cannot connect as root to database
Please install an MTA on this system if you want to use sendmail!
err mail::sending() could not close safefork to sendmail
err List::send_global_file() List::send_global_file, could not send template /usr/share/sympa/default/mail_tt2/listmaster_notification.tt2 to listmaster@user-LatD610
err Log::fatal_err() Unable to send notify 'sympa died' to listmaster
Database sympa defined in sympa.conf has not the right structure or is unreachable. verify db_xxx parameters in sympa.conf
dpkg: error processing sympa (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 sympa
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR][/B]
-------------------------------------------------------------

I've got nothing. Please help!

---

### Post by rkepler on 2012-03-01
I just went through all that with a Sympa migration, and there's something hosed in the package configuration.  All I can remember of the hassle was that it was easier to manually edit the /etc/sympa/sympa.conf for the database and used/passwd and to set everything up manually.  I think I executed the setup script half a dozen times but eventually the package install script showed up during another package install and was happy enough to never come back.

---

