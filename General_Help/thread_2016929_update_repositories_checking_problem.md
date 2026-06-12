---
title: "update repositories checking problem"
date: 2012-07-04
forum: General Help
---

### Post by hyfanious on 2012-07-04
hi
I have 12.04 on my netbook and my problem is that every time I try to check new updates , it downloads all repositories information.
even if u run it for like 4 times in a row it will download the information again and again
what should I do?

---

### Post by matt_symes on 2012-07-05
Hi

Open a terminal and type

```
sudo apt-get update
```Please post the output back here.

Kind regards

---

### Post by hyfanious on 2012-07-05
```
hyfanious@hyfanious:~$ sudo apt-get update
[sudo] password for hyfanious: 
Ign http://archive.ubuntu.com precise InRelease                                                                              
Ign http://archive.ubuntu.com precise-updates InRelease                                                                      
Ign http://archive.ubuntu.com precise-proposed InRelease                                                                     
Ign http://archive.ubuntu.com precise-backports InRelease                                                                    
Ign http://archive.canonical.com precise InRelease                                                                           
Ign http://ppa.launchpad.net precise InRelease                                                                               
Ign http://ppa.launchpad.net precise InRelease                                                                               
Ign http://ppa.launchpad.net precise InRelease                                                                               
Ign http://security.ubuntu.com precise-security InRelease                                                                    
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]                                                                  
Get:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]                                                          
Get:3 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]                                                         
Ign http://ppa.launchpad.net precise InRelease                                                                               
Ign http://ppa.launchpad.net precise InRelease                                                                               
Ign http://ppa.launchpad.net precise InRelease                                                                               
Ign http://ppa.launchpad.net precise InRelease                                                                               
Hit http://archive.canonical.com precise Release.gpg                                                                         
Ign http://extras.ubuntu.com precise InRelease                                                                               
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                             
Get:5 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                   
Get:6 http://archive.ubuntu.com precise-backports Release.gpg [198 B]                                                        
Ign http://www.bunkus.org ./ InRelease                                                                                       
Get:7 http://extras.ubuntu.com precise Release.gpg [72 B]                                                                    
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]                                                          
Get:9 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                   
Get:10 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                  
Hit http://ppa.launchpad.net precise Release.gpg                                                                             
Get:11 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                  
Get:12 http://archive.ubuntu.com precise Release [49.6 kB]                                                                   
Hit http://www.bunkus.org ./ Release.gpg                                                                                     
Hit http://extras.ubuntu.com precise Release                                                                                 
Hit http://archive.canonical.com precise Release                                                                             
Get:13 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                  
Hit http://ppa.launchpad.net precise Release                                                                                 
Ign http://archive.getdeb.net precise-getdeb InRelease                                                                       
Hit http://download.virtualbox.org precise InRelease                                                                         
Hit http://www.bunkus.org ./ Release                                                                                         
Hit http://extras.ubuntu.com precise/main Sources                                                                            
Hit http://archive.canonical.com precise/partner Sources                                                                     
Get:14 http://ppa.launchpad.net precise Release [11.9 kB]                                                                    
Get:15 http://archive.ubuntu.com precise-updates Release [49.6 kB]                                                           
Hit http://www.bunkus.org ./ Sources                                                                                         
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                      
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                   
Hit http://archive.canonical.com precise/partner i386 Packages                                                               
Ign http://archive.canonical.com precise/partner TranslationIndex                                                            
Get:16 http://ppa.launchpad.net precise Release [11.9 kB]                                                                    
Hit http://download.virtualbox.org precise/contrib i386 Packages                                                             
Get:17 http://archive.ubuntu.com precise-proposed Release [49.6 kB]                                                          
Hit http://www.bunkus.org ./ Packages                                                                                        
Get:18 http://ppa.launchpad.net precise Release [11.9 kB]                                                                    
Get:19 http://security.ubuntu.com precise-security/universe Sources [7,832 B]                                                
Hit http://ppa.launchpad.net precise Release                                                                                 
Get:20 http://ppa.launchpad.net precise Release [11.9 kB]                                                                    
Get:21 http://ppa.launchpad.net precise Release [11.9 kB]                                                                    
Get:22 http://archive.getdeb.net precise-getdeb Release.gpg [836 B]                                                          
Ign http://download.virtualbox.org precise/contrib TranslationIndex                                                          
Get:23 http://security.ubuntu.com precise-security/main Sources [22.1 kB]                                                    
Hit http://ppa.launchpad.net precise/main Sources                                                                            
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                      
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                   
Get:24 http://ppa.launchpad.net precise/main Sources [4,135 B]                                                               
Get:25 http://ppa.launchpad.net precise/main i386 Packages [15.2 kB]                                                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                   
Get:26 http://ppa.launchpad.net precise/main Sources [1,294 B]                                                               
Get:27 http://ppa.launchpad.net precise/main i386 Packages [2,584 B]                                                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                   
Get:28 http://archive.ubuntu.com precise-backports Release [49.6 kB]                                                         
Get:29 http://security.ubuntu.com precise-security/restricted Sources [14 B]                                                 
Get:30 http://security.ubuntu.com precise-security/multiverse Sources [713 B]                                                
Get:31 http://security.ubuntu.com precise-security/universe i386 Packages [18.7 kB]                                          
Get:32 http://ppa.launchpad.net precise/main Sources [2,233 B]                                                               
Get:33 http://ppa.launchpad.net precise/main i386 Packages [3,818 B]                                                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                   
Hit http://ppa.launchpad.net precise/main Sources                                                                            
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                      
Get:34 http://security.ubuntu.com precise-security/main i386 Packages [69.5 kB]                                              
Get:35 http://archive.getdeb.net precise-getdeb Release [7,244 B]                                                            
Get:36 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]                                           
Get:37 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]                                        
Get:38 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]                                              
Get:39 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]                                        
Get:40 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]                                        
Get:41 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]                                          
Ign http://www.bunkus.org ./ Translation-en_US                                                                               
Ign http://archive.canonical.com precise/partner Translation-en_US                                                           
Ign http://www.bunkus.org ./ Translation-en                                                                                  
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                  
Get:42 http://security.ubuntu.com precise-security/main Translation-en [35.2 kB]                                             
Ign http://archive.canonical.com precise/partner Translation-en                                                              
Ign http://extras.ubuntu.com precise/main Translation-en                                                                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                   
Get:43 http://ppa.launchpad.net precise/main Sources [23.7 kB]                                                               
Get:44 http://ppa.launchpad.net precise/main i386 Packages [34.4 kB]                                                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                   
Get:45 http://ppa.launchpad.net precise/main Sources [1,337 B]                                                               
Get:46 http://ppa.launchpad.net precise/main i386 Packages [2,159 B]                                                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                   
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                    
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                    
Get:47 http://archive.getdeb.net precise-getdeb/apps i386 Packages [53.1 kB]                                                 
Get:48 http://security.ubuntu.com precise-security/universe Translation-en [12.6 kB]                                         
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                  
Ign http://download.virtualbox.org precise/contrib Translation-en_US                                                         
Ign http://ppa.launchpad.net precise/main Translation-en                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                                     
Get:49 http://archive.ubuntu.com precise/universe Sources [5,019 kB]                                                         
Ign http://download.virtualbox.org precise/contrib Translation-en                                                            
Ign http://archive.getdeb.net precise-getdeb/apps TranslationIndex                                                           
Get:50 http://archive.ubuntu.com precise/main Sources [934 kB]                                                               
Get:51 http://archive.ubuntu.com precise/restricted Sources [5,470 B]                                                        
Get:52 http://archive.ubuntu.com precise/multiverse Sources [155 kB]                                                         
Ign http://archive.getdeb.net precise-getdeb/apps Translation-en_US                                                          
Ign http://archive.getdeb.net precise-getdeb/apps Translation-en                                                             
Get:53 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                                   
Get:54 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                                       
Get:55 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                                  
Get:56 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                                   
Hit http://archive.ubuntu.com precise/main TranslationIndex                                                                  
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex                                                            
Hit http://archive.ubuntu.com precise/restricted TranslationIndex                                                            
Hit http://archive.ubuntu.com precise/universe TranslationIndex                                                              
Get:57 http://archive.ubuntu.com precise-updates/universe Sources [30.9 kB]                                                  
Get:58 http://archive.ubuntu.com precise-updates/main Sources [124 kB]                                                       
Get:59 http://archive.ubuntu.com precise-updates/restricted Sources [1,379 B]                                                
Get:60 http://archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]                                                
Get:61 http://archive.ubuntu.com precise-updates/universe i386 Packages [85.7 kB]                                            
Get:62 http://archive.ubuntu.com precise-updates/main i386 Packages [313 kB]                                                 
Get:63 http://archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]                                          
Get:64 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]                                          
Get:65 http://archive.ubuntu.com precise-updates/main TranslationIndex [74 B]                                                
Get:66 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [71 B]                                          
Get:67 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [71 B]                                          
Get:68 http://archive.ubuntu.com precise-updates/universe TranslationIndex [73 B]                                            
Get:69 http://archive.ubuntu.com precise-proposed/universe Sources [8,249 B]                                                 
Get:70 http://archive.ubuntu.com precise-proposed/main Sources [62.1 kB]                                                     
Get:71 http://archive.ubuntu.com precise-proposed/restricted Sources [14 B]                                                  
Get:72 http://archive.ubuntu.com precise-proposed/multiverse Sources [14 B]                                                  
Get:73 http://archive.ubuntu.com precise-proposed/universe i386 Packages [17.3 kB]                                           
Get:74 http://archive.ubuntu.com precise-proposed/main i386 Packages [150 kB]                                                
Get:75 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]                                            
Get:76 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [14 B]                                            
Get:77 http://archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]                                            
Get:78 http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]                                      
Get:79 http://archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]                                      
Get:80 http://archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]                                        
Get:81 http://archive.ubuntu.com precise-backports/universe Sources [10.3 kB]                                                
Get:82 http://archive.ubuntu.com precise-backports/main Sources [1,845 B]                                                    
Get:83 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]                                                 
Get:84 http://archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]                                              
Get:85 http://archive.ubuntu.com precise-backports/universe i386 Packages [8,940 B]                                          
Get:86 http://archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]                                              
Get:87 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                           
Get:88 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]                                          
Get:89 http://archive.ubuntu.com precise-backports/main TranslationIndex [71 B]                                              
Get:90 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [71 B]                                        
Get:91 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]                                        
Get:92 http://archive.ubuntu.com precise-backports/universe TranslationIndex [72 B]                                          
Hit http://archive.ubuntu.com precise/main Translation-en                                                                    
Hit http://archive.ubuntu.com precise/multiverse Translation-en                                                              
Hit http://archive.ubuntu.com precise/restricted Translation-en                                                              
Hit http://archive.ubuntu.com precise/universe Translation-en                                                                
Get:93 http://archive.ubuntu.com precise-updates/main Translation-en [144 kB]                                                
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en                                                      
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en                                                      
Get:94 http://archive.ubuntu.com precise-updates/universe Translation-en [51.1 kB]                                           
Get:95 http://archive.ubuntu.com precise-proposed/main Translation-en [46.5 kB]                                              
Get:96 http://archive.ubuntu.com precise-proposed/multiverse Translation-en [14 B]                                           
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en                                                     
Get:97 http://archive.ubuntu.com precise-proposed/universe Translation-en [10.3 kB]                                          
Get:98 http://archive.ubuntu.com precise-backports/main Translation-en [908 B]                                               
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en                                                    
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en                                                    
Get:99 http://archive.ubuntu.com precise-backports/universe Translation-en [6,532 B]                                         
Fetched 14.0 MB in 17min 43s (13.2 kB/s)                                                                                     
Reading package lists... Done

```

---

### Post by matt_symes on 2012-07-06
Hi

It does seem to be getting all the update files. I'm not sure why this would be though. :confused:

Have you tried cleaning out your cache, pulling them down again and, after that, seeing if only the ones that have changed are pulled down ?

```
sudo rm /var/lib/apt/lists/*
```

Have you tried a different mirror ?

What are you apt settings ? Do you have any set up ?

Please post the output of

```
grep -v "^//" /etc/apt/apt.conf /etc/apt/apt.conf.d/*
```

Kind regards

---

