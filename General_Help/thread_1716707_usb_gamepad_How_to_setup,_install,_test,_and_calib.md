---
title: "usb gamepad: How to setup, install, test, and calibrate?"
date: 2011-03-28
forum: General Help
---

### Post by Keypel on 2011-03-28
I did some googleing first it said to

```
sudo apt-get install jscalibrator
```

but I get the error E: Unable to locate package jscalibrator

so I'm lost now.

Also, I went to System > Preferences but I only see keyboard and mouse, no gamepad/joystick.

---

### Post by magnetic651 on 2011-03-30
I am having the same problem.  Can anyone help??

---

### Post by Enigmapond on 2011-03-30
Did you install joystick as well? You will need to as that's the package that contains the jscalibrate...I believe. Also this may help.
[http://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-gui-please-in-ubuntu](http://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-gui-please-in-ubuntu)

---

### Post by Keypel on 2011-03-30
> **Enigmapond said:**
> Did you install joystick as well? You will need to as that's the package that contains the jscalibrate...I believe. Also this may help.
[http://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-gui-please-in-ubuntu](http://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-gui-please-in-ubuntu)

Thanks for the reply, the instructions in your link seem very straight forward (compared to the other guides I have read) however I get the error:
"[COLOR="Red"]E: Invalid operation jscalibrator[/COLOR]" after the 3rd step.

```
user-01@pc-01:~$ sudo apt-get update
[sudo] password for user-01: 
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Get:2 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Get:3 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com/opera/ stable/non-free Translation-en                 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Get:4 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US              
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Get:5 http://security.ubuntu.com maverick-security Release [31.4kB]            
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://deb.opera.com stable Release                                        
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:6 http://dl.google.com stable Release [1,347B]                             
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://deb.opera.com stable/non-free i386 Packages                         
Get:7 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]           
Get:8 http://dl.google.com stable/main i386 Packages [1,081B]                  
Get:9 http://security.ubuntu.com maverick-security/main Sources [33.1kB]       
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://deb.opera.com stable/non-free i386 Packages                         
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://us.archive.ubuntu.com maverick/main Sources               
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Get:10 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:11 http://security.ubuntu.com maverick-security/universe Sources [13.4kB]
Get:12 http://security.ubuntu.com maverick-security/multiverse Sources [649B] 
Get:13 http://security.ubuntu.com maverick-security/main i386 Packages [112kB]
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages         
Get:14 http://us.archive.ubuntu.com maverick-updates/main Sources [93.4kB]
Get:15 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:16 http://security.ubuntu.com maverick-security/universe i386 Packages [53.5kB]
Get:17 http://us.archive.ubuntu.com maverick-updates/restricted Sources [778B] 
Get:18 http://us.archive.ubuntu.com maverick-updates/universe Sources [38.8kB] 
Get:19 http://security.ubuntu.com maverick-security/multiverse i386 Packages [1,660B]
Get:20 http://us.archive.ubuntu.com maverick-updates/multiverse Sources [1,496B]
Get:21 http://us.archive.ubuntu.com maverick-updates/main i386 Packages [255kB]
Get:22 http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages [1,797B]
Get:23 http://us.archive.ubuntu.com maverick-updates/universe i386 Packages [114kB]
Get:24 http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,844B]
Fetched 789kB in 5s (148kB/s)                       
Reading package lists... Done
user-01@pc-01:~$ sudo apt-get install joystick
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  evtest
The following NEW packages will be installed:
  evtest joystick
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 49.2kB of archives.
After this operation, 299kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/universe evtest i386 20051019-12 [12.6kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/universe joystick i386 20051019-12 [36.6kB]
Fetched 49.2kB in 1s (45.8kB/s)  
Selecting previously deselected package evtest.
(Reading database ... 151161 files and directories currently installed.)
Unpacking evtest (from .../evtest_20051019-12_i386.deb) ...
Selecting previously deselected package joystick.
Unpacking joystick (from .../joystick_20051019-12_i386.deb) ...
 Removing any system startup links for /etc/init.d/joystick ...
Processing triggers for man-db ...
Setting up evtest (20051019-12) ...
Setting up joystick (20051019-12) ...
user-01@pc-01:~$ sudo apt-get jscalibrator
E: Invalid operation jscalibrator

```

---

### Post by magnetic651 on 2011-03-31
I get the exact same error.

---

### Post by Th3Art0fRu1n on 2011-03-31
I think they quit using jscalibrator. 

> sudo apt-get install joystick> jscal -c /dev/js0

Got my PS3 look-alike controller working.

---

### Post by Keypel on 2011-03-31
> **Th3Art0fRu1n said:**
> I think they quit using jscalibrator. 

```
sudo apt-get install joystick 
```

```
jscal -c /dev/js0 
```

Got my PS3 look-alike controller working.

@Th3Art0fRu1n, after typing the commands you listed, I get the error: "[COLOR="Red"]jscal: can't open joystick device: No such file or directory[/COLOR]"

```
user-01@pc-01:~$ sudo apt-get install joystick
[sudo] password for user-01: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
joystick is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user-01@pc-01:~$ jscal -c /dev/js0
jscal: can't open joystick device: No such file or directory

```

---

### Post by Ryukenden on 2011-11-22
I'm having the same problem with my Sidewinder Gamepad.

---

### Post by jasonripley on 2011-12-22
I just managed to get my Logitech DualAction gamepad working by following the steps given by Th3Art0fRu1n.  I was receiving the "jscal: can't open joystick device: No such file or directory" error mentioned by Keypel.

I needed to use /dev/input/js0 for the commands instead of /dev/js0.

---

### Post by Grumbel on 2012-02-08
As a general rule of thumb: Never ever use jscal or jscalibrator, you don't need them, most games will ignore what you do with them anyway and those that don't have a far higher chance to get worse due to their use then better. 

To make a joystick work in Linux there are really only two steps:

1) plug it in
2) check with dmesg/evtest/jstest that it works

If the above worked and things don't work in a game, it's the games fault.

---

