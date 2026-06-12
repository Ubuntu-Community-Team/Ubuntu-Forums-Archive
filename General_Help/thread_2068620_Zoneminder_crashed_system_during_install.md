---
title: "Zoneminder crashed system during install"
date: 2012-10-09
forum: General Help
---

### Post by Scooby-2 on 2012-10-09
I tried to install Zoneminder on my laptop (which is running 10.04 LTS) using the Ubuntu Software Centre. It got as far as asking me for a password for the mysql database and the system froze shortly afterwards. After about 10 minutes nothing had changed (it was stuck at 78% complete) so I pressed the Cancel button. This brought up a crash report screen which I filled in and told it to send. The progress bar went up to about 10% and the dialogue said something like "Sending crash report." The system froze at this point - no response to the keyboard, the mouse seemed to have disappeared altogether and I couldn't <ctrl><alt>F2 to get a tty login screen. The network and disk activity lights were both off. The power button didn't work so I had to disconnect the power and remove the battery. I rebooted OK and tried to remove and reinstall Zoneminder without success so I searched online. I found a thread here:
[http://ubuntuforums.org/showthread.php?t=1706524](http://ubuntuforums.org/showthread.php?t=1706524)
which said to run the following commands:
```
apt-get purge zoneminder
apt-get clean
apt-get update
apt-get install zoneminder
```My laptop falls at the first hurdle with the following:
> $ sudo apt-get purge zoneminder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  zoneminder*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 6,693kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 240725 files and directories currently installed.)
Removing zoneminder ...
Stopping ZoneMinder: DBI connect('database=zm;host=localhost','zmuser',...) failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/share/perl5/ZoneMinder/Config.pm line 89
Can't call method "prepare_cached" on an undefined value at /usr/share/perl5/ZoneMinder/Config.pm line 91.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/share/perl5/ZoneMinder.pm line 33.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder.pm line 33.
Compilation failed in require at /usr/bin/zmpkg.pl line 45.
BEGIN failed--compilation aborted at /usr/bin/zmpkg.pl line 45.
Zoneminder already stopped

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Purging configuration files for zoneminder ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...Now I get the same error when I try to install or remove anything, not just Zoneminder.
Can anyone help, please?

---

### Post by Scooby-2 on 2012-10-10
Update:
I found an answer to someone having a similar problem and the suggestions included running the following, which I had not tried: 
```
apt-get -f install
apt-get autoremove
apt-get purge
```The results are here:
> root@nx-6325:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up zoneminder (1.24.2-2build3) ...
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nx-6325:~#> root@nx-6325:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up zoneminder (1.24.2-2build3) ...
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nx-6325:~# > root@nx-6325:~# apt-get purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up zoneminder (1.24.2-2build3) ...
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nx-6325:~# 
It seems pretty serious as I get this message whenever I try to remove or install anything.

Looks like I'll have to reinstall. :cry:

P.S. I have a crash file /var/crash/zoneminder.0.crash but it is meaningless to me. Almost 1200 lines of it....

---

### Post by Scooby-2 on 2012-10-10
I found these instructions too:
```
sudo dpkg -r zoneminder 
sudo apt-get -f install 
sudo apt-get update 
sudo apt-get upgrade
```Output:
> root@nx-6325:~# dpkg -r zoneminder
(Reading database ... 240725 files and directories currently installed.)
Removing zoneminder ...
Stopping ZoneMinder: DBI connect('database=zm;host=localhost','zmuser',...) failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/share/perl5/ZoneMinder/Config.pm line 89
Can't call method "prepare_cached" on an undefined value at /usr/share/perl5/ZoneMinder/Config.pm line 91.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/share/perl5/ZoneMinder.pm line 33.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder.pm line 33.
Compilation failed in require at /usr/bin/zmpkg.pl line 45.
BEGIN failed--compilation aborted at /usr/bin/zmpkg.pl line 45.
Zoneminder already stopped

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
root@nx-6325:~# Failed at the first hurdle again. The reinstall looms nearer...

---

### Post by Scooby-2 on 2012-10-10
The commands copied from above:
```
sudo dpkg -r zoneminder  
sudo apt-get -f install  
sudo apt-get update  
sudo apt-get upgrade
```The above commands, despite the first one throwing up errors, did work. The original post solving this problem is here:
[http://askubuntu.com/questions/171205/e-sub-process-usr-bin-dpkg-returned-an-error-code-1](http://askubuntu.com/questions/171205/e-sub-process-usr-bin-dpkg-returned-an-error-code-1)

Thanks to [jokerdino]("http://askubuntu.com/users/25798/jokerdino") for his post there. [IMG]http://i235.photobucket.com/albums/ee40/Haffie2kd/smiley/icon_smile_wink.gif[/IMG]

---

### Post by Scooby-2 on 2012-10-11
As I seem to be the only one with this problem I'll keep it  up-to-date so I can review it later!

I'm  on a good hiding to nothing, Zoneminder won't install because mysql  won't run on 10.04/my machine. I've spent all day and most of last night  trying suggestions which others have offered for the same problem, to  no avail. I struggle enough with Linux but the database side of it is  way beyond me so I'm just trying things blindly. It's clearly a very common problem with different solutions and there is no way to tell which one may work.

I am planning to  upgrade to 12.04.1 LTS anyway but the bad news is that Zoneminder  doesn't run on that version either - see  [https://bugs.launchpad.net/ubuntu/+source/zoneminder/+bug/995157](https://bugs.launchpad.net/ubuntu/+source/zoneminder/+bug/995157) - and  it sounds like it's exactly the same problem. There are no real  alternatives for Linux when using an IP camera (except Motion, which  supports ONLY Axis, ACTi and Canon cameras without rebuilding the  application from source).

The only alternative seems to be Windows and iSpy from [http://www.ispyconnect.com/](http://www.ispyconnect.com/) At least it's free but I hate the insecurity of Windows, not to mention the cost.

---

