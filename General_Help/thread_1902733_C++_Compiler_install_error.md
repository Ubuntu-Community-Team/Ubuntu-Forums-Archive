---
title: "C++ Compiler install error"
date: 2011-12-31
forum: General Help
---

### Post by optima4 on 2011-12-31
Hello

 why when installing C++ compiler I get this error?

```
sudo aptitude install build-essential
[sudo] password: 
sudo: aptitude: command not found

```

---

### Post by Doug S on 2011-12-31
I think the command should be:```
sudo apt-get install build-essential
```

---

### Post by oldos2er on 2011-12-31
> **optima4 said:**
> Hello

 why when installing C++ compiler I get this error?

```
sudo aptitude install build-essential
[sudo] password: 
sudo: aptitude: command not found

```

aptitude is not installed by default in 11.10. If you want it, run ```
sudo apt-get update && sudo apt-get install aptitude && sudo aptitude install build-essential
```

---

### Post by optima4 on 2011-12-31
> **oldos2er said:**
> aptitude is not installed by default in 11.10. If you want it, run ```
sudo apt-get update && sudo apt-get install aptitude && sudo aptitude install build-essential
```

Ah ha, that did something.

```
ll aptitude && sudo aptitude install build-essential
[sudo] password for plethoraviao: 
Ign http://extras.ubuntu.com oneiric InRelease                                 
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://deb.torproject.org experimental-lucid InRelease                     
Hit http://deb.torproject.org experimental-lucid/main i386 Packages            
Ign http://deb.torproject.org experimental-lucid/main TranslationIndex         
Ign http://deb.torproject.org experimental-lucid/main Translation-en_US        
Ign http://deb.torproject.org experimental-lucid/main Translation-en           
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:2 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Get:3 http://ppa.launchpad.net oneiric Release [9,756 B]                       
Get:4 http://ppa.launchpad.net oneiric/main Sources [702 B]                    
Get:5 http://ppa.launchpad.net oneiric/main i386 Packages [1,255 B]            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://mirrors.melbourne.co.uk oneiric InRelease                     
Ign http://mirrors.melbourne.co.uk oneiric-updates InRelease                   
Ign http://mirrors.melbourne.co.uk oneiric-backports InRelease                 
Ign http://mirrors.melbourne.co.uk oneiric-security InRelease                  
Hit http://mirrors.melbourne.co.uk oneiric Release.gpg                         
Hit http://mirrors.melbourne.co.uk oneiric-updates Release.gpg                 
Hit http://mirrors.melbourne.co.uk oneiric-backports Release.gpg               
Hit http://mirrors.melbourne.co.uk oneiric-security Release.gpg                
Hit http://mirrors.melbourne.co.uk oneiric Release                             
Hit http://mirrors.melbourne.co.uk oneiric-updates Release                     
Hit http://mirrors.melbourne.co.uk oneiric-backports Release                   
Hit http://mirrors.melbourne.co.uk oneiric-security Release                    
Hit http://mirrors.melbourne.co.uk oneiric/main Sources                        
Hit http://mirrors.melbourne.co.uk oneiric/restricted Sources                  
Hit http://mirrors.melbourne.co.uk oneiric/universe Sources                    
Hit http://mirrors.melbourne.co.uk oneiric/multiverse Sources                  
Hit http://mirrors.melbourne.co.uk oneiric/main i386 Packages                  
Hit http://mirrors.melbourne.co.uk oneiric/restricted i386 Packages            
Hit http://mirrors.melbourne.co.uk oneiric/universe i386 Packages              
Hit http://mirrors.melbourne.co.uk oneiric/multiverse i386 Packages            
Hit http://mirrors.melbourne.co.uk oneiric/main TranslationIndex               
Hit http://mirrors.melbourne.co.uk oneiric/multiverse TranslationIndex         
Hit http://mirrors.melbourne.co.uk oneiric/restricted TranslationIndex         
Hit http://mirrors.melbourne.co.uk oneiric/universe TranslationIndex           
Hit http://mirrors.melbourne.co.uk oneiric-updates/main Sources                
Hit http://mirrors.melbourne.co.uk oneiric-updates/restricted Sources          
Hit http://mirrors.melbourne.co.uk oneiric-updates/universe Sources            
Hit http://mirrors.melbourne.co.uk oneiric-updates/multiverse Sources          
Hit http://mirrors.melbourne.co.uk oneiric-updates/main i386 Packages          
Hit http://mirrors.melbourne.co.uk oneiric-updates/restricted i386 Packages    
Hit http://mirrors.melbourne.co.uk oneiric-updates/universe i386 Packages      
Hit http://mirrors.melbourne.co.uk oneiric-updates/multiverse i386 Packages    
Hit http://mirrors.melbourne.co.uk oneiric-updates/main TranslationIndex       
Hit http://mirrors.melbourne.co.uk oneiric-updates/multiverse TranslationIndex 
Hit http://mirrors.melbourne.co.uk oneiric-updates/restricted TranslationIndex 
Hit http://mirrors.melbourne.co.uk oneiric-updates/universe TranslationIndex   
Hit http://mirrors.melbourne.co.uk oneiric-backports/main Sources              
Hit http://mirrors.melbourne.co.uk oneiric-backports/restricted Sources        
Hit http://mirrors.melbourne.co.uk oneiric-backports/universe Sources          
Hit http://mirrors.melbourne.co.uk oneiric-backports/multiverse Sources        
Hit http://mirrors.melbourne.co.uk oneiric-backports/main i386 Packages        
Hit http://mirrors.melbourne.co.uk oneiric-backports/restricted i386 Packages  
Hit http://mirrors.melbourne.co.uk oneiric-backports/universe i386 Packages    
Hit http://mirrors.melbourne.co.uk oneiric-backports/multiverse i386 Packages  
Hit http://mirrors.melbourne.co.uk oneiric-backports/main TranslationIndex     
Hit http://mirrors.melbourne.co.uk oneiric-backports/multiverse TranslationIndex
Hit http://mirrors.melbourne.co.uk oneiric-backports/restricted TranslationIndex
Hit http://mirrors.melbourne.co.uk oneiric-backports/universe TranslationIndex 
Hit http://mirrors.melbourne.co.uk oneiric-security/main Sources               
Hit http://mirrors.melbourne.co.uk oneiric-security/restricted Sources         
Hit http://mirrors.melbourne.co.uk oneiric-security/universe Sources           
Hit http://mirrors.melbourne.co.uk oneiric-security/multiverse Sources         
Hit http://mirrors.melbourne.co.uk oneiric-security/main i386 Packages         
Hit http://mirrors.melbourne.co.uk oneiric-security/restricted i386 Packages
Hit http://mirrors.melbourne.co.uk oneiric-security/universe i386 Packages
Hit http://mirrors.melbourne.co.uk oneiric-security/multiverse i386 Packages
Hit http://mirrors.melbourne.co.uk oneiric-security/main TranslationIndex
Hit http://mirrors.melbourne.co.uk oneiric-security/multiverse TranslationIndex
Hit http://mirrors.melbourne.co.uk oneiric-security/restricted TranslationIndex
Hit http://mirrors.melbourne.co.uk oneiric-security/universe TranslationIndex
Hit http://mirrors.melbourne.co.uk oneiric/main Translation-en
Hit http://mirrors.melbourne.co.uk oneiric/multiverse Translation-en
Hit http://mirrors.melbourne.co.uk oneiric/restricted Translation-en
Hit http://mirrors.melbourne.co.uk oneiric/universe Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-updates/main Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-updates/multiverse Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-updates/restricted Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-updates/universe Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-backports/main Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-backports/multiverse Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-backports/restricted Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-backports/universe Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-security/main Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-security/multiverse Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-security/restricted Translation-en
Hit http://mirrors.melbourne.co.uk oneiric-security/universe Translation-en
Ign http://deb.opera.com stable InRelease              
Hit http://deb.opera.com stable Release.gpg
Hit http://deb.opera.com stable Release
Hit http://deb.opera.com stable/non-free i386 Packages
Ign http://deb.opera.com stable/non-free TranslationIndex
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en
Fetched 12.1 kB in 23s (511 B/s)
Reading package lists... Done
W: Duplicate sources.list entry http://deb.torproject.org/torproject.org/ experimental-lucid/main i386 Packages (/var/lib/apt/lists/deb.torproject.org_torproject.org_dists_experimental-lucid_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,850 kB of archives.
After this operation, 8,835 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mirrors.melbourne.co.uk/ubuntu/ oneiric/main libboost-iostreams1.46.1 i386 1.46.1-5ubuntu2 [40.2 kB]
Get:2 http://mirrors.melbourne.co.uk/ubuntu/ oneiric/main libcwidget3 i386 0.5.16-3.1ubuntu1 [392 kB]
Get:3 http://mirrors.melbourne.co.uk/ubuntu/ oneiric/main aptitude i386 0.6.4-1ubuntu2 [2,316 kB]
Get:4 http://mirrors.melbourne.co.uk/ubuntu/ oneiric/main libsub-name-perl i386 0.05-1build1 [10.6 kB]
Get:5 http://mirrors.melbourne.co.uk/ubuntu/ oneiric/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:6 http://mirrors.melbourne.co.uk/ubuntu/ oneiric/main libio-string-perl all 1.08-2 [12.0 kB]
Get:7 http://mirrors.melbourne.co.uk/ubuntu/ oneiric/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Fetched 2,850 kB in 5s (484 kB/s)                   
Selecting previously deselected package libboost-iostreams1.46.1.
(Reading database ... 222325 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-5ubuntu2_i386.deb) ...
Selecting previously deselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_i386.deb) ...
Selecting previously deselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.05-1build1_i386.deb) ...
Selecting previously deselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously deselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously deselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up libboost-iostreams1.46.1 (1.46.1-5ubuntu2) ...
Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up aptitude (0.6.4-1ubuntu2) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.05-1build1) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```
I got these perfect results, but then I tried to run the file again and have the same error of 

"no such file directory"

If you dont mind I accidentally added another thread like this can you please help me only on there? [http://ubuntuforums.org/showthread.php?t=1902814](http://ubuntuforums.org/showthread.php?t=1902814)

Thank you

---

