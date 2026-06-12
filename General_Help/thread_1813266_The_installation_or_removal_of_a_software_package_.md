---
title: "The installation or removal of a software package failed."
date: 2011-07-27
forum: General Help
---

### Post by brijit on 2011-07-27
I am new to Ubuntu. I am using Ubuntu 10.10

I tried to install software (Gmail Notifier) through 'Ubuntu Software Center'

I don't know why I am getting following error message :

[COLOR=Red](Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 failed to read on buffer copy for files list for package `libtaglib2.0-cil': Input/output error [/COLOR]

Even if I tried to remove any software I am getting this error.

Also when I want to change 'Visual Effects' to 'Normal' or 'Extra' through 'Appearance Preferences'.....first it shows 'searching for available drivers' and then the message : 

[COLOR=Red]Desktop effects could not be enabled[/COLOR]

Pls help me to rectify.

---

### Post by brijit on 2011-07-28
Also it seems my 'Compiz' and 'Metacity' are not working properly

Pls help

---

### Post by wildmanne39 on 2011-07-28
Hi, that an be a very hard problem to fix, first open disk utility and run a smart test on your drive and see if there are any errors, that is one of the causes of that error, then you can run these commands on at a time and see if it fixes the problem.
```
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
```
if you get errors please post them here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by brijit on 2011-07-28
Dear [wildmanne39]("http://ubuntuforums.org/member.php?u=508533")

I encountered the same error

[COLOR=Red]# brijit@brijit-Aspire-5740:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg [198B]                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Get:6 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                 
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Get:7 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg [198B]         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [9,762B]                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31.4kB]           
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,775B]                      
Get:13 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release [39.8kB]                  
Get:15 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,962B]          
Get:16 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,774B]    
Get:17 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,774B]    
Get:18 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources [1,073B]                 
Get:19 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages [1,216B]           
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,750B]                      
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release [31.4kB]          
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [24.8kB]                 
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources [829kB]              
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [28.0kB]           
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [46.2kB]      
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [19.4kB]  
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [1,758B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [155kB] 
Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [634B]                   
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [591B]             
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [76.3kB]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [3,746B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources [4,179kB]        
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources [151kB]        
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages [1,492kB]      
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages [5,992B] 
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages [5,791kB]  
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages [183kB]  
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources [137kB]      
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources [46.8kB] 
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources [2,506B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages [378kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages [156kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [5,206B]
Fetched 13.9MB in 4min 38s (49.9kB/s)                                          
Reading package lists... Done
brijit@brijit-Aspire-5740:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cups evolution-plugins linux-generic linux-headers-generic
  linux-image-generic
The following packages will be upgraded:
  dbus dbus-x11 libdbus-1-3 libfreetype6 libpng12-0 libsndfile1
6 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/1,136kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 failed to read on buffer copy for files list for package `libtaglib2.0-cil': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/COLOR]
I have done 'Self Test' through 'Disk Utility' but it doesn't complete, so I had to Cancel.

Also when I did 'Check File System' then I had this error :
[COLOR=Red]Device is mounted and no online capability in fsck tool for file system[/COLOR]

Pls suggest some remedy.

Thanx for your support.

---

### Post by wildmanne39 on 2011-07-28
Hi, look at this link and do what it says, if it does not work I recommend formating your drive and reinstalling.
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

