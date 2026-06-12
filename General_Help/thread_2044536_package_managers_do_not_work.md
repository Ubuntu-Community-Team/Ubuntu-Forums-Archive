---
title: "package managers do not work"
date: 2012-08-19
forum: General Help
---

### Post by jlh68 on 2012-08-19
Since the last 12.04LTS update (Linux 3.2.0.29) neither Ubuntu Software Center nor Synaptic Package Manager will work.  They load onto the screen until the load is finished and then they just dissapear.  I now cannot add or delete applications.

What happened?

---

### Post by oldos2er on 2012-08-19
Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal, and post the output here?

---

### Post by jlh68 on 2012-08-19
I also have the following warning from Synaptic Package Manager, see the attached image.

> john@Nighthawk:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for john: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                              
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                             
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]                   
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                             
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                                 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                                                         
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                                                                
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                                                                  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                                  
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                              
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                                                                 
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                                                                 
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                                                                 
Get:15 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [4,181 B]                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                                             
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                               
Get:17 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages [5,146 B]                                                          
Get:18 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [5,140 B]                                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                                
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                            
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                  
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [39.7 kB]                                                       
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                         
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [720 B]                                                                               
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [739 B]                                                                                  
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [731 B]                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                           
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [720 B]                                                                    
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [719 B]                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                             
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [18.4 kB]                                                                  
Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [18.4 kB]                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                        
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [7,243 B]                               
Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [7,237 B]                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                          
Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [655 B]                                                         
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [655 B]                                                                  
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]                                                      
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [10.2 kB]                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                     
Get:36 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [4,185 B]                                          
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [4,196 B]                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                        
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [524 B]                                             
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [524 B]                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                             
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B]                                                        
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [156 kB]                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                             
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [39.4 kB]
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,180 B]      
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [160 kB]            
Get:46 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]   
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [39.6 kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]        
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [73 B]              
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]           
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]                                                                
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]                                                                  
Get:54 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [74.2 kB]                                                                     
Get:55 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [995 B]                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                                                              
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]                                                                              
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]                                                                           
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]                                                                      
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB]                                                                       
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB]                                                                       
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]                                                                            
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]                                                                       
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]                                                                        
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                                                                   
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [157 kB]                                                                            
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]                                                                     
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [47.6 kB]                                                                       
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]                                                                     
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [372 kB]                                                                     
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [6,755 B]                                                              
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [123 kB]                                                                 
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,677 B]                                                              
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [376 kB]                                                                      
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]                                                               
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [123 kB]                                                                  
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]                                                               
Get:77 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                                                                  
Get:78 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                                                            
Get:79 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                                                            
Get:80 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                                                              
Get:81 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]                                                                         
Get:82 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                                                      
Get:83 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [13.1 kB]                                                                     
Get:84 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]                                                                   
Get:85 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]                                                                  
Get:86 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]                                                               
Get:87 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [11.7 kB]                                                              
Get:88 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [996 B]                                                              
Get:89 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]                                                                   
Get:90 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                                                
Get:91 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [11.7 kB]                                                               
Get:92 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                                                     
Get:93 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [180 kB]                                                                     
Get:94 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [5,414 B]                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                           
Get:95 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [73.5 kB]                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                                                           
Fetched 20.8 MB in 1min 21s (255 kB/s)                                                                                                               
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
john@Nighthawk:~$ 

---

### Post by unevenflow on 2012-08-19
Try this

```
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*; sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists; sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean; sudo apt-get autoclean
sudo apt-get update
```

---

### Post by jlh68 on 2012-08-20
Your solution worked.
Would you briefly explain each line, so that I will have an idea of what happened and how it was corrected?

Thanks.
John

---

