---
title: "Problem with mysql"
date: 2011-01-24
forum: General Help
---

### Post by neokyle on 2011-01-24
So ive installed mysql server on my server running ubuntu 9.10 64 bit. I checked to see if the mysql server was running and it was not so i attempted to start it. I got "[fail]"

So i tried reinstalling it.

sudo apt-get --reinstall install mysql-server

That didnt work so i did the following.

sudo apt-get --purge remove mysql-server
sudo apt-get install mysql-server

That did not work so i googled the issue and found a dead thread saying to run the following and post the outcome which has now lead me here to the lovely ubuntu support forums :) 

dpkg -l | grep -v ^ii

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                      Description
+++-=================================-============================-============================================
iU  mysql-server                      5.1.37-1ubuntu5.5            MySQL database server (metapackage depending
iF  mysql-server-5.1                  5.1.37-1ubuntu5.5            MySQL database server binaries

Thanks in advance for the help :)

---

### Post by cavh on 2011-01-24
Probably easiest to reinstall using tasksel and choose the LAMP server install - this will install an Apache/MySQL/phpMyAdmin combination. In a terminal window:

```
sudo tasksel
```

and select LAMP using the space bar to check box. DO NOT remove the check from the Ubuntu desktop box as this will remove your graphical desktop.

---

### Post by neokyle on 2011-01-24
still getting

invoke-rc.d: initscript mysql, action "start" failed.

---

### Post by cavh on 2011-01-24
Sorry, can't help you further. Suggest posting in the Server Platforms forum at [http://ubuntuforums.org/forumdisplay.php?f=339]("http://ubuntuforums.org/forumdisplay.php?f=339")

---

