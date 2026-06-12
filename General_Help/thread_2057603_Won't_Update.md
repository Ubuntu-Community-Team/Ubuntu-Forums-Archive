---
title: "Won't Update?"
date: 2012-09-14
forum: General Help
---

### Post by Yezinki on 2012-09-14
Hi there,

There is an update present but Software updater won't install it...any ideas, clues, suggestions?

[IMG]http://i4.photobucket.com/albums/y129/eDOC/Screenshotfrom2012-09-13015158.png[/IMG]

Thanks.

---

### Post by 2F4U on 2012-09-14
Any error message? What happens if you do from a terminal

sudo apt-get update
sudo apt-get upgrade

If you are getting errors, post them here.

---

### Post by dino99 on 2012-09-14
no needs to post duplicate thread here & into the "upgrade" subforum
already answered

---

### Post by Yezinki on 2012-09-14
```
vaio@VGC-LS1:~$ sudo apt-get update
[sudo] password for vaio: 
Ign http://mirror-cybernet.lums.edu.pk precise InRelease
Hit http://mirror-cybernet.lums.edu.pk precise Release.gpg                     
Ign http://dl.google.com stable InRelease                                      
Get:1 http://packages.medibuntu.org precise InRelease [7,096 B]                
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.canonical.com precise InRelease                             
Hit http://mirror-cybernet.lums.edu.pk precise Release                         
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://packages.medibuntu.org precise InRelease                            
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://mirror-cybernet.lums.edu.pk precise/main Sources                    
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise Release.gpg                               
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://archive.canonical.com precise Release                               
Ign http://deb.opera.com stable InRelease                                      
Hit http://mirror-cybernet.lums.edu.pk precise/restricted Sources              
Ign http://ppa.launchpad.net precise Release.gpg                               
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex         
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Ign http://extras.ubuntu.com precise InRelease                                 
Get:7 http://dl.google.com stable/main i386 Packages [1,239 B]                 
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://mirror-cybernet.lums.edu.pk precise/universe Sources                
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:8 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://mirror-cybernet.lums.edu.pk precise/multiverse Sources              
Hit http://deb.opera.com stable Release                                        
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Ign http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://mirror-cybernet.lums.edu.pk precise/main i386 Packages              
Hit http://extras.ubuntu.com precise Release                                   
Hit http://deb.opera.com stable/non-free i386 Packages                         
Get:9 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://mirror-cybernet.lums.edu.pk precise/restricted i386 Packages        
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main Sources                              
Get:10 http://security.ubuntu.com precise-security/main Sources [42.8 kB]      
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://mirror-cybernet.lums.edu.pk precise/universe i386 Packages          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://mirror-cybernet.lums.edu.pk precise/multiverse i386 Packages        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://mirror-cybernet.lums.edu.pk precise/main TranslationIndex           
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Hit http://mirror-cybernet.lums.edu.pk precise/multiverse TranslationIndex     
Hit http://mirror-cybernet.lums.edu.pk precise/restricted TranslationIndex     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://mirror-cybernet.lums.edu.pk precise/universe TranslationIndex       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://mirror-cybernet.lums.edu.pk precise/main Translation-en             
Get:11 http://us.archive.ubuntu.com precise-updates/main Sources [164 kB]      
Hit http://mirror-cybernet.lums.edu.pk precise/multiverse Translation-en       
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Hit http://mirror-cybernet.lums.edu.pk precise/restricted Translation-en       
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://mirror-cybernet.lums.edu.pk precise/universe Translation-en         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.canonical.com precise/partner Translation-en                
Get:12 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:13 http://security.ubuntu.com precise-security/universe Sources [13.5 kB]  
Get:14 http://security.ubuntu.com precise-security/multiverse Sources [1,386 B]
Get:15 http://security.ubuntu.com precise-security/main i386 Packages [165 kB] 
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:16 http://us.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Get:17 http://us.archive.ubuntu.com precise-updates/universe Sources [51.8 kB] 
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:18 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:19 http://us.archive.ubuntu.com precise-updates/main i386 Packages [388 kB]
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                        
  404  Not Found
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                        
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:20 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:21 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [131 kB]
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [43.9 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Get:25 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Get:26 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:27 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:28 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:29 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Ign http://packages.medibuntu.org precise/free Translation-en                  
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Get:30 http://us.archive.ubuntu.com precise-updates/main Translation-en [188 kB]
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:31 http://us.archive.ubuntu.com precise-updates/universe Translation-en [77.7 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 1,419 kB in 19s (72.3 kB/s)                                            
W: GPG error: http://packages.medibuntu.org precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
vaio@VGC-LS1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ginn libavcodec-extra-53 libavutil-extra-51 libgrip0 mencoder mplayer
The following packages will be upgraded:
  eog
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 763 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main eog i386 3.4.2-0ubuntu1.1 [763 kB]
Fetched 763 kB in 8s (86.2 kB/s)                                               
(Reading database ... 281574 files and directories currently installed.)
Preparing to replace eog 3.4.2-0ubuntu1 (using .../eog_3.4.2-0ubuntu1.1_i386.deb) ...
Unpacking replacement eog ...
Processing triggers for menu ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up eog (3.4.2-0ubuntu1.1) ...
Processing triggers for menu ...
vaio@VGC-LS1:~$ 

```

---

