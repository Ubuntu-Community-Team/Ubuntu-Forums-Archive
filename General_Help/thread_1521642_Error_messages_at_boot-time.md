---
title: "Error messages at boot-time"
date: 2010-07-01
forum: General Help
---

### Post by diego_pmc on 2010-07-01
I just upgraded to 10.04 through the Update Manager. During the updated however I got an error telling me that it was unable to install something. Sorry, I can't remember what it was; it didn't stop the updated so I assumed it wasn't that important. :oops:

Anyways, I don't know if this is because of that error, but during the boot process and when shutting the computer I get console messages. When I boot it tells me that "mounting none on /dev failed No such device" and when I shut down I get [these messages]("http://img693.imageshack.us/f/01072010304.jpg/").

I see [this was asked before]("http://ubuntuforums.org/showthread.php?t=1435968") and that it isn't a big issue, but I'd still like to solve it. The problem is that I'm pretty new to Ubuntu and Linux in general I don't know how to follow the very general instructions given in that thread. Could someone please be more explicit about what steps I should take to fix this?

---

### Post by dino99 on 2010-07-01
open a console (apps accessories terminal) and run:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

more info about Lucid following the links below

---

### Post by diego_pmc on 2010-07-01
Thanks for the reply! 
This doesn't seem to fix the problem however. When I request the updates ([FONT="Lucida Console"]sudo apt-get update[/FONT]) I get a list of several files, but when I try to install them ([FONT="Lucida Console"]sudo apt-get install -f[/FONT]) it tells me that "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.". Consequently, when I try to configure ([FONT="Lucida Console"]sudo dpkg --configure -a[/FONT]) nothing happens.

```
**paul@MANTAPC:~$ sudo apt-get update**
[sudo] password for paul: 
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://security.ubuntu.com lucid-security Release.gpg                
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US    
Get:2 http://dl.google.com stable Release [2,544B]                   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Get:3 http://dl.google.com stable/main Packages [1,052B]             
Hit http://security.ubuntu.com lucid-security/main Packages              
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://ro.archive.ubuntu.com lucid Release.gpg
Ign http://ro.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://ro.archive.ubuntu.com lucid-updates Release.gpg
Ign http://ro.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://ro.archive.ubuntu.com lucid Release
Hit http://ro.archive.ubuntu.com lucid-updates Release
Hit http://ro.archive.ubuntu.com lucid/main Packages
Hit http://ro.archive.ubuntu.com lucid/restricted Packages
Hit http://ro.archive.ubuntu.com lucid/main Sources
Hit http://ro.archive.ubuntu.com lucid/restricted Sources
Hit http://ro.archive.ubuntu.com lucid/universe Packages
Hit http://ro.archive.ubuntu.com lucid/universe Sources
Hit http://ro.archive.ubuntu.com lucid/multiverse Packages
Hit http://ro.archive.ubuntu.com lucid/multiverse Sources
Hit http://ro.archive.ubuntu.com lucid-updates/main Packages
Hit http://ro.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://ro.archive.ubuntu.com lucid-updates/main Sources
Hit http://ro.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://ro.archive.ubuntu.com lucid-updates/universe Packages
Hit http://ro.archive.ubuntu.com lucid-updates/universe Sources
Hit http://ro.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://ro.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 3,785B in 0s (5,045B/s)
Reading package lists... Done
**paul@MANTAPC:~$ sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**paul@MANTAPC:~$ sudo dpkg --configure -a**
paul@MANTAPC:~$ 
```

---

