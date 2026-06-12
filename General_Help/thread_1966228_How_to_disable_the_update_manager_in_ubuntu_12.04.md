---
title: "How to disable the update manager in ubuntu 12.04"
date: 2012-04-26
forum: General Help
---

### Post by sky5564 on 2012-04-26
I want to disable it, I find it annoying and useless, Updating via the terminal is so much easier and faster so tell me how i might go about disabling it?

---

### Post by papibe on 2012-04-26
Hi sky5564.

There are seem to be several ways to accomplish this. These are what I think are the most simple:

First, to stop it from popping up: go to 'Startup Applications' and disable the 'Update Notifier'.

Then to avoid double work (the 'check' option that does apt-get update): open 'Update Manager' and press 'Settings'. There is section called 'Automatic Update'. There, change the field 'Check for updates' from 'Daily' to 'Never' (or uncheck the field on 10.04).

I hope that helps, and tell us how it goes.
Regards.

---

### Post by techsupport on 2012-04-26
> **sky5564 said:**
> I want to disable it, I find it annoying and useless, Updating via the terminal is so much easier and faster so tell me how i might go about disabling it?

Yes, Startup Applications lists all of the programs running in the "tray" at login.  Just disable whatever you don't want running in the background.

---

### Post by sky5564 on 2012-04-26
> **papibe said:**
> Hi sky5564.

There are seem to be several ways to accomplish this. These are what I think are the most simple:

First, to stop it from popping up: go to 'Startup Applications' and disable the 'Update Notifier'.

Then to avoid double work (the 'check' option that does apt-get update): open 'Update Manager' and press 'Settings'. There is section called 'Automatic Update'. There, change the field 'Check for updates' from 'Daily' to 'Never' (or uncheck the field on 10.04).

I hope that helps, and tell us how it goes.
Regards.

Well i went to startup applications but it was empty, But i went to the update manager and selected weekly updates instead of daily so maybe that will be good enough to stop the daily nagging lol.

Thanks guys this solved my problem.

---

### Post by kgarbutt on 2012-05-01
Cut & paste this into the terminal:

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

After this, then reopen 'Startup Applications' and all will be good.

Enjoy.

---

### Post by JKyleOKC on 2012-05-01
It's always a good idea to explain exactly what any suggested command line does, since it's so easy to destroy a system by giving out a malicious command. The one by kgarbutt is fine, and helpful -- I mean no criticism of his helpfulness, just a general suggestion to everyone.

Here's what it does: The *.desktop files in the /etc/xdg/autostart directory are the launchers for each listed process, and some but not all of them contain the line "NoDisplay=true" to prevent them from being displayed in the Autostart dialog. His command simply changes that line from "true" to "false" in any desktop file that contains it, so that all of the launchers appear in the dialog and can be enabled or disabled. It's a highly powerful technique!

---

### Post by Sepero on 2012-05-09
> **kgarbutt said:**
> 
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop


Much appreciated!

---

### Post by Enigmapond on 2012-05-09
> **kgarbutt said:**
> Cut & paste this into the terminal:

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

After this, then reopen 'Startup Applications' and all will be good.

Enjoy.

Sweet! Thanx for that!

---

### Post by emagar on 2012-07-09
A related question from a Linux newbie.

I've been updating from the shell with apt-get update then apt-get upgrade. I recently did this right after the update manager prompted me to perform several upgrades. I moved to the shell instead. 

I then re-opened the update manager to verify that the list of upgrades was indeed empty. To my amazement, it was not (after pushing the check button)... How can apt-get be missing updates scheduled in the update manager?

Thanks in advance,

---

### Post by JKyleOKC on 2012-07-09
Did you click the "Check" button in Update Manager after doing the update through the terminal? This should force the program to compare the latest version in the repository to those in your machine, and update its list of pending updates accordingly. It doesn't do that checking automatically...

---

### Post by emagar on 2012-07-10
Thanks JKyleOKC. I, in fact, did push the check button. Hence my amazement. I'll see if the system does it again in a couple of days with fresh upgrades and report.

---

### Post by emagar on 2012-07-19
> **JKyleOKC said:**
> Did you click the "Check" button in Update Manager after doing the update through the terminal? This should force the program to compare the latest version in the repository to those in your machine, and update its list of pending updates accordingly. It doesn't do that checking automatically...

It's happened again. Ran sudo apt-get update and sudo apt-get upgrade minutes ago. 

```
eric@eric-xps13:~/Dropbox/data/vetopol/usa/escritos/postate$ sudo apt-get update 
Ign http://cran.itam.mx precise/ InRelease
Get:1 http://cran.itam.mx precise/ Release.gpg [490 B]                 
Ign http://security.ubuntu.com precise-security InRelease              
Ign http://extras.ubuntu.com precise InRelease                         
Ign http://ppa.launchpad.net precise InRelease                         
Ign http://ppa.launchpad.net precise InRelease                         
Ign http://mx.archive.ubuntu.com precise InRelease                     
Ign http://mx.archive.ubuntu.com precise-updates InRelease             
Ign http://mx.archive.ubuntu.com precise-backports InRelease           
Get:2 http://cran.itam.mx precise/ Release [2,280 B]                   
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]  
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]              
Hit http://ppa.launchpad.net precise Release.gpg                       
Get:5 http://mx.archive.ubuntu.com precise Release.gpg [198 B]         
Get:6 http://mx.archive.ubuntu.com precise-updates Release.gpg [198 B] 
Hit http://cran.itam.mx precise/ Sources                               
Get:7 http://security.ubuntu.com precise-security Release [49.6 kB]    
Hit http://ppa.launchpad.net precise Release.gpg                       
Hit http://extras.ubuntu.com precise Release                           
Get:8 http://mx.archive.ubuntu.com precise-backports Release.gpg [198 B]
Hit http://cran.itam.mx precise/ Packages                              
Ign http://archive.canonical.com precise InRelease                     
Hit http://ppa.launchpad.net precise Release                           
Hit http://extras.ubuntu.com precise/main Sources                      
Get:9 http://mx.archive.ubuntu.com precise Release [49.6 kB]           
Hit http://archive.canonical.com precise Release.gpg                   
Hit http://ppa.launchpad.net precise Release                           
Hit http://extras.ubuntu.com precise/main amd64 Packages               
Hit http://extras.ubuntu.com precise/main i386 Packages                
Hit http://archive.canonical.com precise Release                       
Hit http://ppa.launchpad.net precise/main Sources                      
Ign http://extras.ubuntu.com precise/main TranslationIndex             
Hit http://ppa.launchpad.net precise/main amd64 Packages               
Hit http://ppa.launchpad.net precise/main i386 Packages                
Ign http://ppa.launchpad.net precise/main TranslationIndex             
Hit http://archive.canonical.com precise/partner Sources               
Get:10 http://security.ubuntu.com precise-security/main Sources [30.0 kB]
Get:11 http://mx.archive.ubuntu.com precise-updates Release [49.6 kB]  
Hit http://ppa.launchpad.net precise/main Sources                      
Hit http://ppa.launchpad.net precise/main amd64 Packages               
Hit http://ppa.launchpad.net precise/main i386 Packages                
Ign http://ppa.launchpad.net precise/main TranslationIndex             
Hit http://archive.canonical.com precise/partner amd64 Packages        
Hit http://archive.canonical.com precise/partner i386 Packages         
Ign http://archive.canonical.com precise/partner TranslationIndex      
Get:12 http://mx.archive.ubuntu.com precise-backports Release [49.6 kB]
Get:13 http://security.ubuntu.com precise-security/restricted Sources [14 B]
Get:14 http://security.ubuntu.com precise-security/universe Sources [7,849 B]
Get:15 http://security.ubuntu.com precise-security/multiverse Sources [713 B]
Get:16 http://security.ubuntu.com precise-security/main amd64 Packages [95.0 kB]
Get:17 http://mx.archive.ubuntu.com precise/main Sources [934 kB]      
Get:18 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:19 http://security.ubuntu.com precise-security/universe amd64 Packages [24.2 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Get:21 http://security.ubuntu.com precise-security/main i386 Packages [97.6 kB]
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [24.4 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:25 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:26 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:27 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:28 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Ign http://cran.itam.mx precise/ Translation-en_US                     
Get:29 http://security.ubuntu.com precise-security/main Translation-en [50.5 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Ign http://cran.itam.mx precise/ Translation-en                        
Get:30 http://mx.archive.ubuntu.com precise/restricted Sources [5,470 B]
Get:31 http://mx.archive.ubuntu.com precise/universe Sources [5,019 kB]
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:32 http://security.ubuntu.com precise-security/universe Translation-en [15.6 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US            
Ign http://archive.canonical.com precise/partner Translation-en_US     
Ign http://extras.ubuntu.com precise/main Translation-en               
Ign http://archive.canonical.com precise/partner Translation-en        
Ign http://ppa.launchpad.net precise/main Translation-en_US            
Ign http://ppa.launchpad.net precise/main Translation-en    
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en    
Get:33 http://mx.archive.ubuntu.com precise/multiverse Sources [155 kB]
Get:34 http://mx.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get:35 http://mx.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:36 http://mx.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]
Get:37 http://mx.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]
Get:38 http://mx.archive.ubuntu.com precise/main i386 Packages [1,274 kB]
Get:39 http://mx.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]
Get:40 http://mx.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]
Get:41 http://mx.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]
Hit http://mx.archive.ubuntu.com precise/main TranslationIndex         
Hit http://mx.archive.ubuntu.com precise/multiverse TranslationIndex   
Hit http://mx.archive.ubuntu.com precise/restricted TranslationIndex   
Hit http://mx.archive.ubuntu.com precise/universe TranslationIndex     
Get:42 http://mx.archive.ubuntu.com precise-updates/main Sources [132 kB]
Get:43 http://mx.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:44 http://mx.archive.ubuntu.com precise-updates/universe Sources [36.4 kB]
Get:45 http://mx.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:46 http://mx.archive.ubuntu.com precise-updates/main amd64 Packages [328 kB]
Get:47 http://mx.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]
Get:48 http://mx.archive.ubuntu.com precise-updates/universe amd64 Packages [94.7 kB]
Get:49 http://mx.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,829 B]
Get:50 http://mx.archive.ubuntu.com precise-updates/main i386 Packages [330 kB]
Get:51 http://mx.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:52 http://mx.archive.ubuntu.com precise-updates/universe i386 Packages [95.1 kB]
Get:53 http://mx.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Get:54 http://mx.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:55 http://mx.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:56 http://mx.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:57 http://mx.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:58 http://mx.archive.ubuntu.com precise-backports/main Sources [1,845 B]
Get:59 http://mx.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:60 http://mx.archive.ubuntu.com precise-backports/universe Sources [12.4 kB]
Get:61 http://mx.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:62 http://mx.archive.ubuntu.com precise-backports/main amd64 Packages [1,271 B]
Get:63 http://mx.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:64 http://mx.archive.ubuntu.com precise-backports/universe amd64 Packages [11.1 kB]
Get:65 http://mx.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]
Get:66 http://mx.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:67 http://mx.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:68 http://mx.archive.ubuntu.com precise-backports/universe i386 Packages [11.2 kB]
Get:69 http://mx.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://mx.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://mx.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://mx.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://mx.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://mx.archive.ubuntu.com precise/main Translation-en           
Hit http://mx.archive.ubuntu.com precise/multiverse Translation-en     
Hit http://mx.archive.ubuntu.com precise/restricted Translation-en     
Hit http://mx.archive.ubuntu.com precise/universe Translation-en       
Get:70 http://mx.archive.ubuntu.com precise-updates/main Translation-en [155 kB]
Hit http://mx.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://mx.archive.ubuntu.com precise-updates/restricted Translation-en
Get:71 http://mx.archive.ubuntu.com precise-updates/universe Translation-en [56.9 kB]
Hit http://mx.archive.ubuntu.com precise-backports/main Translation-en 
Hit http://mx.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://mx.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://mx.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 20.3 MB in 20s (1,008 kB/s)                                    
Reading package lists... Done
eric@eric-xps13:~/Dropbox/data/vetopol/usa/escritos/postate$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  hplip hplip-data libhpmud0 libsane-hpaio printer-driver-hpcups
  printer-driver-hpijs
The following packages will be upgraded:
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5
  libkidletime4 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4
  libkrosscore4 libktexteditor4 libnepomuk4 libnepomukquery4a
  libnepomukutils4 libplasma3 libsolid4 libthreadweaver4 libtiff4
  libtiff4:i386 xkb-data
36 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 13.4 MB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mx.archive.ubuntu.com/ubuntu/ precise-updates/main xkb-data all 2.5-1ubuntu1.3 [474 kB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/main libtiff4 i386 3.9.5-2ubuntu1.2 [142 kB]
Get:3 http://security.ubuntu.com/ubuntu/ precise-security/main libtiff4 amd64 3.9.5-2ubuntu1.2 [144 kB]
Get:4 http://security.ubuntu.com/ubuntu/ precise-security/main libplasma3 amd64 4:4.8.4a-0ubuntu0.2 [892 kB]
Get:5 http://security.ubuntu.com/ubuntu/ precise-security/main libknotifyconfig4 amd64 4:4.8.4a-0ubuntu0.2 [39.8 kB]
Get:6 http://security.ubuntu.com/ubuntu/ precise-security/main libknewstuff3-4 amd64 4:4.8.4a-0ubuntu0.2 [154 kB]
Get:7 http://security.ubuntu.com/ubuntu/ precise-security/main libkfile4 amd64 4:4.8.4a-0ubuntu0.2 [218 kB]
Get:8 http://security.ubuntu.com/ubuntu/ precise-security/main libkemoticons4 amd64 4:4.8.4a-0ubuntu0.2 [41.4 kB]
Get:9 http://security.ubuntu.com/ubuntu/ precise-security/main libkdewebkit5 amd64 4:4.8.4a-0ubuntu0.2 [61.6 kB]
Get:10 http://security.ubuntu.com/ubuntu/ precise-security/main libkde3support4 amd64 4:4.8.4a-0ubuntu0.2 [301 kB]
Get:11 http://security.ubuntu.com/ubuntu/ precise-security/main kdoctools amd64 4:4.8.4a-0ubuntu0.2 [171 kB]
Get:12 http://security.ubuntu.com/ubuntu/ precise-security/main kdelibs-bin amd64 4:4.8.4a-0ubuntu0.2 [201 kB]
Get:13 http://security.ubuntu.com/ubuntu/ precise-security/main libkio5 amd64 4:4.8.4a-0ubuntu0.2 [835 kB]
Get:14 http://security.ubuntu.com/ubuntu/ precise-security/main libnepomuk4 amd64 4:4.8.4a-0ubuntu0.2 [214 kB]
Get:15 http://security.ubuntu.com/ubuntu/ precise-security/main libkmediaplayer4 amd64 4:4.8.4a-0ubuntu0.2 [29.4 kB]
Get:16 http://security.ubuntu.com/ubuntu/ precise-security/main libkrosscore4 amd64 4:4.8.4a-0ubuntu0.2 [57.4 kB]
Get:17 http://security.ubuntu.com/ubuntu/ precise-security/main libkdesu5 amd64 4:4.8.4a-0ubuntu0.2 [51.9 kB]
Get:18 http://security.ubuntu.com/ubuntu/ precise-security/main libkpty4 amd64 4:4.8.4a-0ubuntu0.2 [33.2 kB]
Get:19 http://security.ubuntu.com/ubuntu/ precise-security/main libkntlm4 amd64 4:4.8.4a-0ubuntu0.2 [28.4 kB]
Get:20 http://security.ubuntu.com/ubuntu/ precise-security/main libkjsembed4 amd64 4:4.8.4a-0ubuntu0.2 [340 kB]
Get:21 http://security.ubuntu.com/ubuntu/ precise-security/main libkjsapi4 amd64 4:4.8.4a-0ubuntu0.2 [235 kB]
Get:22 http://security.ubuntu.com/ubuntu/ precise-security/main libkidletime4 amd64 4:4.8.4a-0ubuntu0.2 [38.1 kB]
Get:23 http://security.ubuntu.com/ubuntu/ precise-security/main libkdnssd4 amd64 4:4.8.4a-0ubuntu0.2 [67.7 kB]
Get:24 http://security.ubuntu.com/ubuntu/ precise-security/main libkdeclarative5 amd64 4:4.8.4a-0ubuntu0.2 [37.9 kB]
Get:25 http://security.ubuntu.com/ubuntu/ precise-security/main libkcmutils4 amd64 4:4.8.4a-0ubuntu0.2 [94.0 kB]
Get:26 http://security.ubuntu.com/ubuntu/ precise-security/main libkdeui5 amd64 4:4.8.4a-0ubuntu0.2 [1,282 kB]
Get:27 http://security.ubuntu.com/ubuntu/ precise-security/main libkdecore5 amd64 4:4.8.4a-0ubuntu0.2 [916 kB]
Get:28 http://security.ubuntu.com/ubuntu/ precise-security/main kdelibs5-data all 4:4.8.4a-0ubuntu0.2 [2,832 kB]
Get:29 http://security.ubuntu.com/ubuntu/ precise-security/main kdelibs5-plugins amd64 4:4.8.4a-0ubuntu0.2 [927 kB]
Get:30 http://security.ubuntu.com/ubuntu/ precise-security/main libkhtml5 amd64 4:4.8.4a-0ubuntu0.2 [1,886 kB]
Get:31 http://security.ubuntu.com/ubuntu/ precise-security/main libktexteditor4 amd64 4:4.8.4a-0ubuntu0.2 [94.2 kB]
Get:32 http://security.ubuntu.com/ubuntu/ precise-security/main libkparts4 amd64 4:4.8.4a-0ubuntu0.2 [118 kB]
Get:33 http://security.ubuntu.com/ubuntu/ precise-security/main libnepomukutils4 amd64 4:4.8.4a-0ubuntu0.2 [86.9 kB]
Get:34 http://security.ubuntu.com/ubuntu/ precise-security/main libnepomukquery4a amd64 4:4.8.4a-0ubuntu0.2 [109 kB]
Get:35 http://security.ubuntu.com/ubuntu/ precise-security/main libsolid4 amd64 4:4.8.4a-0ubuntu0.2 [248 kB]
Get:36 http://security.ubuntu.com/ubuntu/ precise-security/main libthreadweaver4 amd64 4:4.8.4a-0ubuntu0.2 [46.5 kB]
Fetched 13.4 MB in 10s (1,224 kB/s)                                    
Extracting templates from packages: 100%
(Reading database ... 321189 files and directories currently installed.)
Preparing to replace libtiff4:i386 3.9.5-2ubuntu1.1 (using .../libtiff4_3.9.5-2ubuntu1.2_i386.deb) ...
De-configuring libtiff4 ...
Unpacking replacement libtiff4:i386 ...
Preparing to replace libtiff4 3.9.5-2ubuntu1.1 (using .../libtiff4_3.9.5-2ubuntu1.2_amd64.deb) ...
Unpacking replacement libtiff4 ...
Setting up libtiff4:i386 (3.9.5-2ubuntu1.2) ...
Setting up libtiff4 (3.9.5-2ubuntu1.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 321189 files and directories currently installed.)
Preparing to replace xkb-data 2.5-1ubuntu1 (using .../xkb-data_2.5-1ubuntu1.3_all.deb) ...
Unpacking replacement xkb-data ...
Preparing to replace libplasma3 4:4.8.4a-0ubuntu0.1 (using .../libplasma3_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libplasma3 ...
Preparing to replace libknotifyconfig4 4:4.8.4a-0ubuntu0.1 (using .../libknotifyconfig4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libknotifyconfig4 ...
Preparing to replace libknewstuff3-4 4:4.8.4a-0ubuntu0.1 (using .../libknewstuff3-4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libknewstuff3-4 ...
Preparing to replace libkfile4 4:4.8.4a-0ubuntu0.1 (using .../libkfile4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkfile4 ...
Preparing to replace libkemoticons4 4:4.8.4a-0ubuntu0.1 (using .../libkemoticons4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkemoticons4 ...
Preparing to replace libkdewebkit5 4:4.8.4a-0ubuntu0.1 (using .../libkdewebkit5_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkdewebkit5 ...
Preparing to replace libkde3support4 4:4.8.4a-0ubuntu0.1 (using .../libkde3support4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkde3support4 ...
Preparing to replace kdoctools 4:4.8.4a-0ubuntu0.1 (using .../kdoctools_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement kdoctools ...
Preparing to replace kdelibs-bin 4:4.8.4a-0ubuntu0.1 (using .../kdelibs-bin_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement kdelibs-bin ...
Preparing to replace libkio5 4:4.8.4a-0ubuntu0.1 (using .../libkio5_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkio5 ...
Preparing to replace libnepomuk4 4:4.8.4a-0ubuntu0.1 (using .../libnepomuk4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libnepomuk4 ...
Preparing to replace libkmediaplayer4 4:4.8.4a-0ubuntu0.1 (using .../libkmediaplayer4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkmediaplayer4 ...
Preparing to replace libkrosscore4 4:4.8.4a-0ubuntu0.1 (using .../libkrosscore4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkrosscore4 ...
Preparing to replace libkdesu5 4:4.8.4a-0ubuntu0.1 (using .../libkdesu5_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkdesu5 ...
Preparing to replace libkpty4 4:4.8.4a-0ubuntu0.1 (using .../libkpty4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkpty4 ...
Preparing to replace libkntlm4 4:4.8.4a-0ubuntu0.1 (using .../libkntlm4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkntlm4 ...
Preparing to replace libkjsembed4 4:4.8.4a-0ubuntu0.1 (using .../libkjsembed4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkjsembed4 ...
Preparing to replace libkjsapi4 4:4.8.4a-0ubuntu0.1 (using .../libkjsapi4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkjsapi4 ...
Preparing to replace libkidletime4 4:4.8.4a-0ubuntu0.1 (using .../libkidletime4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkidletime4 ...
Preparing to replace libkdnssd4 4:4.8.4a-0ubuntu0.1 (using .../libkdnssd4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkdnssd4 ...
Preparing to replace libkdeclarative5 4:4.8.4a-0ubuntu0.1 (using .../libkdeclarative5_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkdeclarative5 ...
Preparing to replace libkcmutils4 4:4.8.4a-0ubuntu0.1 (using .../libkcmutils4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkcmutils4 ...
Preparing to replace libkdeui5 4:4.8.4a-0ubuntu0.1 (using .../libkdeui5_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkdeui5 ...
Preparing to replace libkdecore5 4:4.8.4a-0ubuntu0.1 (using .../libkdecore5_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkdecore5 ...
Preparing to replace kdelibs5-data 4:4.8.4a-0ubuntu0.1 (using .../kdelibs5-data_4%3a4.8.4a-0ubuntu0.2_all.deb) ...
Unpacking replacement kdelibs5-data ...
Preparing to replace kdelibs5-plugins 4:4.8.4a-0ubuntu0.1 (using .../kdelibs5-plugins_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement kdelibs5-plugins ...
Preparing to replace libkhtml5 4:4.8.4a-0ubuntu0.1 (using .../libkhtml5_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkhtml5 ...
Preparing to replace libktexteditor4 4:4.8.4a-0ubuntu0.1 (using .../libktexteditor4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libktexteditor4 ...
Preparing to replace libkparts4 4:4.8.4a-0ubuntu0.1 (using .../libkparts4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libkparts4 ...
Preparing to replace libnepomukutils4 4:4.8.4a-0ubuntu0.1 (using .../libnepomukutils4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libnepomukutils4 ...
Preparing to replace libnepomukquery4a 4:4.8.4a-0ubuntu0.1 (using .../libnepomukquery4a_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libnepomukquery4a ...
Preparing to replace libsolid4 4:4.8.4a-0ubuntu0.1 (using .../libsolid4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libsolid4 ...
Preparing to replace libthreadweaver4 4:4.8.4a-0ubuntu0.1 (using .../libthreadweaver4_4%3a4.8.4a-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libthreadweaver4 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme ...
Setting up xkb-data (2.5-1ubuntu1.3) ...
Setting up libkdecore5 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkdeui5 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkcmutils4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libnepomuk4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libsolid4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkio5 (4:4.8.4a-0ubuntu0.2) ...
Setting up libnepomukquery4a (4:4.8.4a-0ubuntu0.2) ...
Setting up libnepomukutils4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkparts4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkdewebkit5 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkdnssd4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libknewstuff3-4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libthreadweaver4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libplasma3 (4:4.8.4a-0ubuntu0.2) ...
Setting up libknotifyconfig4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkfile4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkemoticons4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkpty4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkde3support4 (4:4.8.4a-0ubuntu0.2) ...
Setting up kdoctools (4:4.8.4a-0ubuntu0.2) ...
Setting up libkjsapi4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkjsembed4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkrosscore4 (4:4.8.4a-0ubuntu0.2) ...
Setting up kdelibs-bin (4:4.8.4a-0ubuntu0.2) ...
Setting up libkmediaplayer4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkdesu5 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkntlm4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkidletime4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkdeclarative5 (4:4.8.4a-0ubuntu0.2) ...
Setting up kdelibs5-data (4:4.8.4a-0ubuntu0.2) ...
Setting up libktexteditor4 (4:4.8.4a-0ubuntu0.2) ...
Setting up libkhtml5 (4:4.8.4a-0ubuntu0.2) ...
Setting up kdelibs5-plugins (4:4.8.4a-0ubuntu0.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```When done, I noticed that the Update manager had popped with its own list of upgrades. I pushed the 'check' button, expecting an empty list. I instead got this:

---

### Post by JKyleOKC on 2012-07-19
My browser doesn't show the screen shot in large enough format for my ancient eyes to read all of it, but it looks as if update-manager is only displaying the "recommended" packages including "hplip" and its dependencies.

And the log of your apt-get session shows that those packages were held back and NOT updated, probably because they were already on the list created by update-manager although this is just a guess on my part.

At this point I would do one of two things: if you are actually using hplip to support HP equipment such as a printer or a scanner, I would have update-manager install the group that it still has checked. If not, I would use synaptic to "completely remove" the hplip package from the system, then use "apt-get autoremove" and "apt-get autoclean" to get rid of any of its dependencies that might be left over.

This is all, however, guesswork since I don't mix use of the update manager and apt-get for routine updates. I simply let update-manager do its thing, and use apt-get only for house-cleaning and occasional special needs.

---

### Post by ljungkvist on 2012-08-25
> **kgarbutt said:**
> Cut & paste this into the terminal:

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

After this, then reopen 'Startup Applications' and all will be good.

Enjoy.

Thanks, but why the hell do you need to do this? Why are all of these hidden by default? Weird and stupid!

---

### Post by twipley on 2012-09-14
Perhaps because the devs dislike the idea of laymans fiddling with such elements, which constitute the building stones of a functional system.

By the way, the command is neat, and I also think it should be like this by default.

---

### Post by twipley on 2012-09-15
Let one head over to Brainstorm and add their vote!

[[IMG]http://brainstorm.ubuntu.com/idea/29961/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/29961/)

---

### Post by beejee on 2012-09-20
> **emagar said:**
> It's happened again. Ran sudo apt-get update and sudo apt-get upgrade minutes ago. 


You can run ***sudo apt-get dist-upgrade*** to install those held back packages from the command prompt.
Over [_here_:KS]("http://www.debian-administration.org/articles/69") you can find a decent explanation why those packages are being held back.

---

### Post by bart.a on 2012-10-13
thanks.. this worked for me to..

---

### Post by ibawolf on 2012-12-07
to do the same update from the command-line, that the update manager does.  Use the command:

  apt-get dist-upgrade



> **emagar said:**
> A related question from a Linux newbie.

I've been updating from the shell with apt-get update then apt-get upgrade. I recently did this right after the update manager prompted me to perform several upgrades. I moved to the shell instead. 

I then re-opened the update manager to verify that the list of upgrades was indeed empty. To my amazement, it was not (after pushing the check button)... How can apt-get be missing updates scheduled in the update manager?

Thanks in advance,

---

