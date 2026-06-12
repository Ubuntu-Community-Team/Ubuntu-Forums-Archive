---
title: "Error when trying too update"
date: 2012-03-24
forum: General Help
---

### Post by CarlWalters on 2012-03-24
I'm trying to run a software update on my Ubunu 11.10 system but I'm running into problems. If I run update manager I get error screen as the image with the error message

```

The following packages have unmet dependencies:

libsclang1: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed
            Depends: libscsynth1 but it is not installed

```

If I run sudo apt-get -f install then I get 

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libscsynth1
The following NEW packages will be installed
  libscsynth1
0 upgraded, 1 newly installed, 0 to remove and 68 not upgraded.
2 not fully installed or removed.
Need to get 0 B/164 kB of archives.
After this operation, 430 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 294708 files and directories currently installed.)
Unpacking libscsynth1 (from .../libscsynth1_1%3a3.4.4-2ubuntu3~oneiric0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libscsynth1_1%3a3.4.4-2ubuntu3~oneiric0_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libscsynth.so.1', which is also in package supercollider-server 1:3.4.4-0ubuntu2~oneiric3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libscsynth1_1%3a3.4.4-2ubuntu3~oneiric0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
carl@carl-Dell-DXC051:~$ 


```

and sudo apt-get update gives the following#

```

carl@carl-Dell-DXC051:~$ sudo apt-get update
Ign http://gb.archive.ubuntu.com oneiric InRelease
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                                                                                                                                                    
Ign http://gb.archive.ubuntu.com oneiric-backports InRelease                                                                                                                                                  
Ign http://archive.canonical.com oneiric InRelease                                                                                                                                                            
Ign http://security.ubuntu.com oneiric-security InRelease                                                                                                                                                     
Hit http://packages.medibuntu.org oneiric InRelease                                                                                                                                                           
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                                                                                                                                               
Hit http://gb.archive.ubuntu.com oneiric-updates Release.gpg                                                                                                            
Hit http://archive.canonical.com oneiric Release.gpg                                                                                                                                             
Hit http://security.ubuntu.com oneiric-security Release.gpg                                                                                                                                      
Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg                                                                                                          
Hit http://gb.archive.ubuntu.com oneiric Release                                                                                                                        
Hit http://archive.canonical.com oneiric Release                                                                                                                                                                     
Ign http://extras.ubuntu.com oneiric InRelease                                                                                                                                                                       
Ign http://ubuntuarchive.eweka.nl oneiric InRelease                                                                                                                                            
Ign http://ubuntuarchive.eweka.nl oneiric-updates InRelease                                                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric-updates Release                                                                                                      
Hit http://security.ubuntu.com oneiric-security Release                                                                                
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                                
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                                
Ign http://ppa.launchpad.net oneiric InRelease                                                                                          
Hit http://gb.archive.ubuntu.com oneiric-backports Release                                                                                                    
Ign http://ubuntuarchive.eweka.nl oneiric-security InRelease                                                                                                  
Hit http://packages.medibuntu.org oneiric/free i386 Packages                                                                                                  
Get:1 http://ubuntuarchive.eweka.nl oneiric Release.gpg [198 B]                                                                                               
Hit http://archive.canonical.com oneiric/partner i386 Packages                                                                          
Hit http://gb.archive.ubuntu.com oneiric/main Sources                                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                                                                                                              
Hit http://gb.archive.ubuntu.com oneiric/universe Sources                                                                                                                
Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                                                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                                                                                                                                    
Hit http://extras.ubuntu.com oneiric Release.gpg                                                                                                                                               
Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages                                                                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                                                                                                                                                      
Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages                                                                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                                                                                                                                                       
Ign http://archive.canonical.com oneiric/partner TranslationIndex                                                                                                                                                    
Get:2 http://ubuntuarchive.eweka.nl oneiric-updates Release.gpg [198 B]                                                                                                                                              
Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex                                                                                                                           
Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex                                                                                         
Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex                                                                                           
Hit http://gb.archive.ubuntu.com oneiric-updates/main Sources                                                                                                
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Sources                                                                                          
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                               
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                               
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                               
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                               
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                               
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Sources                                                                                            
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                               
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                               
Hit http://security.ubuntu.com oneiric-security/main Sources                                                                                                 
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages                                                                                             
Get:3 http://ubuntuarchive.eweka.nl oneiric-security Release.gpg [198 B]                                                                                                                      
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources                                                                                                                           
Hit http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages                                                                                                                           
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages                                                                                                                     
Hit http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages                                                                                                                       
Hit http://extras.ubuntu.com oneiric Release                                                                                                                                                  
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages                                                                                                                     
Hit http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex                                                                                                                         
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex                                                                                                                   
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex                                                                                                                   
Hit http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex                                                                                                                     
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                                                                 
Hit http://security.ubuntu.com oneiric-security/restricted Sources                                                                                                                             
Hit http://security.ubuntu.com oneiric-security/universe Sources                                                                                                        
Hit http://security.ubuntu.com oneiric-security/multiverse Sources                                                                                                                            
Hit http://security.ubuntu.com oneiric-security/main i386 Packages                                                                                                                            
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages                                                                                                                      
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                                              
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                        
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                             
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                             
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                             
Get:4 http://ubuntuarchive.eweka.nl oneiric Release [40.8 kB]                                                                                                
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB                                                                                                      
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en                                                                                                         
Hit http://gb.archive.ubuntu.com oneiric-backports/main Sources                                                                                                      
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Sources                                                                                                
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Sources                                                                                                  
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Sources                                                                          
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages                                                                          
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages                                                                        
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex                                                                                                 
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex                                                                                           
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex                                                                                           
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                                                                                                       
Hit http://extras.ubuntu.com oneiric/main Sources                                                                                               
Hit http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages                                                                                                            
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages                                                                                                      
Hit http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages                                                                                                        
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages                                                                                                       
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                                                        
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                                                        
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                                  
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                                  
Hit http://gb.archive.ubuntu.com oneiric-backports/main TranslationIndex                                                                                                                                
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex                                                                                                                          
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted TranslationIndex                                                                                                                          
Hit http://gb.archive.ubuntu.com oneiric-backports/universe TranslationIndex                                                                                                                            
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB                                                                                                                                   
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex                                                                                                                               
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                                                        
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                                  
Hit http://ppa.launchpad.net oneiric Release                                                                                                     
Hit http://ppa.launchpad.net oneiric Release                                                                                                     
Hit http://ppa.launchpad.net oneiric Release                                                                                                     
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en                                                                               
Hit http://security.ubuntu.com oneiric-security/main Translation-en                                                                                                                           
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en                                                                                                                     
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB                                                                                                                         
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en                                                                                                     
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en                                                                                                       
Hit http://gb.archive.ubuntu.com oneiric-updates/main Translation-en                                                                                                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                                                                                                
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                                                                                             
Hit http://ppa.launchpad.net oneiric Release                                                                                                                           
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                                                                             
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en                                                                       
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en                                                                         
Hit http://gb.archive.ubuntu.com oneiric-backports/main Translation-en                                                                           
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en                                                                                                                                                      
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en                                                                                                                            
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en                                                                                                                            
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en                                                                                                                              
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                                                                                                                                 
Hit http://ppa.launchpad.net oneiric Release                                                                                                                                      
Hit http://ppa.launchpad.net oneiric Release                                                                               
Hit http://ppa.launchpad.net oneiric Release                                                                               
Hit http://ppa.launchpad.net oneiric Release                                                                               
Hit http://ppa.launchpad.net oneiric Release                                                                               
Get:5 http://ubuntuarchive.eweka.nl oneiric-updates Release [40.8 kB]                                                                             
Hit http://ppa.launchpad.net oneiric Release                                                                                                      
Hit http://ppa.launchpad.net oneiric Release                                                                                                                 
Ign http://archive.canonical.com oneiric/partner Translation-en_GB                                                                                                                   
Get:6 http://ubuntuarchive.eweka.nl oneiric-security Release [40.8 kB]                                                                                                               
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                             
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                                             
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                          
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                   
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                                             
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                          
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                   
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                                             
Ign http://archive.canonical.com oneiric/partner Translation-en                                                                                     
Get:7 http://ubuntuarchive.eweka.nl oneiric/main Sources [877 kB]                                                                                   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                               
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                   
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                             
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                         
Hit http://ppa.launchpad.net oneiric/main Sources                                                  
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                         
Hit http://ppa.launchpad.net oneiric/main Sources                                                  
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                   
Hit http://ppa.launchpad.net oneiric/main Sources                                                             
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                       
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                   
Hit http://ppa.launchpad.net oneiric/main Sources                                                  
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                         
Hit http://ppa.launchpad.net oneiric/main Sources                                                  
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                         
Hit http://ppa.launchpad.net oneiric/main Sources                                                  
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                         
Hit http://ppa.launchpad.net oneiric/main Sources                                                  
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                         
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                                        
Ign http://extras.ubuntu.com oneiric/main Translation-en                                                      
Get:8 http://ubuntuarchive.eweka.nl oneiric/restricted Sources [5,351 B]                                      
Get:9 http://ubuntuarchive.eweka.nl oneiric/universe Sources [4,677 kB]                              
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB                                     
Ign http://packages.medibuntu.org oneiric/free Translation-en                                                                         
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB                                                                  
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                                                                          
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                                             
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                                                                          
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                                             
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                                         
Ign http://ppa.launchpad.net oneiric/main Translation-en                                            
Ign http://packages.medibuntu.org oneiric/non-free Translation-en                                   
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                                         
Ign http://ppa.launchpad.net oneiric/main Translation-en                      
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                   
Ign http://ppa.launchpad.net oneiric/main Translation-en                      
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                   
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                   
Ign http://ppa.launchpad.net oneiric/main Translation-en                      
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                   
Ign http://ppa.launchpad.net oneiric/main Translation-en                      
Get:10 http://ubuntuarchive.eweka.nl oneiric/multiverse Sources [149 kB]      
Get:11 http://ubuntuarchive.eweka.nl oneiric/main i386 Packages [1,226 kB]
Get:12 http://ubuntuarchive.eweka.nl oneiric/restricted i386 Packages [8,216 B]                                                                                                                                                               
Get:13 http://ubuntuarchive.eweka.nl oneiric/universe i386 Packages [4,468 kB]                                                                                                                                                                
Get:14 http://ubuntuarchive.eweka.nl oneiric/multiverse i386 Packages [119 kB]                                                                                                                                                                
Get:15 http://ubuntuarchive.eweka.nl oneiric/main TranslationIndex [3,289 B]                                                                                                                                                                  
Get:16 http://ubuntuarchive.eweka.nl oneiric/multiverse TranslationIndex [2,265 B]                                                                                                                                                            
Get:17 http://ubuntuarchive.eweka.nl oneiric/restricted TranslationIndex [2,263 B]                                                                                                                                                            
Get:18 http://ubuntuarchive.eweka.nl oneiric/universe TranslationIndex [2,640 B]                                                                                                                                                              
Get:19 http://ubuntuarchive.eweka.nl oneiric-updates/main Sources [132 kB]                                                                                                                                                                    
Get:20 http://ubuntuarchive.eweka.nl oneiric-updates/restricted Sources [1,337 B]                                                                                                                                                             
Get:21 http://ubuntuarchive.eweka.nl oneiric-updates/universe Sources [48.8 kB]                                                                                                                                                               
Get:22 http://ubuntuarchive.eweka.nl oneiric-updates/multiverse Sources [3,648 B]                                                                                                                                                             
Get:23 http://ubuntuarchive.eweka.nl oneiric-updates/main i386 Packages [305 kB]                                                                                                                                                              
Get:24 http://ubuntuarchive.eweka.nl oneiric-updates/restricted i386 Packages [2,968 B]                                                                                                                                                       
Get:25 http://ubuntuarchive.eweka.nl oneiric-updates/universe i386 Packages [105 kB]                                                                                                                                                          
Get:26 http://ubuntuarchive.eweka.nl oneiric-updates/multiverse i386 Packages [6,367 B]                                                                                                                                                       
Get:27 http://ubuntuarchive.eweka.nl oneiric-updates/main TranslationIndex [74 B]                                                                                                                                                             
Get:28 http://ubuntuarchive.eweka.nl oneiric-updates/multiverse TranslationIndex [72 B]                                                                                                                                                       
Get:29 http://ubuntuarchive.eweka.nl oneiric-updates/restricted TranslationIndex [71 B]                                                                                                                                                       
Get:30 http://ubuntuarchive.eweka.nl oneiric-updates/universe TranslationIndex [73 B]                                                                                                                                                         
Get:31 http://ubuntuarchive.eweka.nl oneiric-security/main Sources [34.5 kB]                                                                                                                                                                  
Get:32 http://ubuntuarchive.eweka.nl oneiric-security/restricted Sources [14 B]                                                                                                                                                               
Get:33 http://ubuntuarchive.eweka.nl oneiric-security/universe Sources [13.3 kB]                                                                                                                                                              
Get:34 http://ubuntuarchive.eweka.nl oneiric-security/multiverse Sources [1,654 B]                                                                                                                                                            
Get:35 http://ubuntuarchive.eweka.nl oneiric-security/main i386 Packages [90.5 kB]                                                                                                                                                            
Get:36 http://ubuntuarchive.eweka.nl oneiric-security/restricted i386 Packages [14 B]                                                                                                                                                         
Get:37 http://ubuntuarchive.eweka.nl oneiric-security/universe i386 Packages [31.4 kB]                                                                                                                                                        
Get:38 http://ubuntuarchive.eweka.nl oneiric-security/multiverse i386 Packages [3,363 B]                                                                                                                                                      
Get:39 http://ubuntuarchive.eweka.nl oneiric-security/main TranslationIndex [73 B]                                                                                                                                                            
Get:40 http://ubuntuarchive.eweka.nl oneiric-security/multiverse TranslationIndex [72 B]                                                                                                                                                      
Get:41 http://ubuntuarchive.eweka.nl oneiric-security/restricted TranslationIndex [70 B]                                                                                                                                                      
Get:42 http://ubuntuarchive.eweka.nl oneiric-security/universe TranslationIndex [73 B]                                                                                                                                                        
Get:43 http://ubuntuarchive.eweka.nl oneiric/main Translation-en_GB [69.0 kB]                                                                                                                                                                 
Get:44 http://ubuntuarchive.eweka.nl oneiric/main Translation-en [701 kB]                                                                                                                                                                     
Get:45 http://ubuntuarchive.eweka.nl oneiric/multiverse Translation-en_GB [68.5 kB]                                                                                                                                                           
Get:46 http://ubuntuarchive.eweka.nl oneiric/multiverse Translation-en [92.6 kB]                                                                                                                                                              
Get:47 http://ubuntuarchive.eweka.nl oneiric/restricted Translation-en_GB [1,937 B]                                                                                                                                                           
Get:48 http://ubuntuarchive.eweka.nl oneiric/restricted Translation-en [2,229 B]                                                                                                                                                              
Get:49 http://ubuntuarchive.eweka.nl oneiric/universe Translation-en_GB [4,365 B]                                                                                                                                                             
Get:50 http://ubuntuarchive.eweka.nl oneiric/universe Translation-en [3,165 kB]                                                                                                                                                               
Get:51 http://ubuntuarchive.eweka.nl oneiric-updates/main Translation-en [142 kB]                                                                                                                                                             
Get:52 http://ubuntuarchive.eweka.nl oneiric-updates/multiverse Translation-en [3,524 B]                                                                                                                                                      
Get:53 http://ubuntuarchive.eweka.nl oneiric-updates/restricted Translation-en [508 B]                                                                                                                                                        
Get:54 http://ubuntuarchive.eweka.nl oneiric-updates/universe Translation-en [62.9 kB]                                                                                                                                                        
Get:55 http://ubuntuarchive.eweka.nl oneiric-security/main Translation-en [50.7 kB]                                                                                                                                                           
Get:56 http://ubuntuarchive.eweka.nl oneiric-security/multiverse Translation-en [1,494 B]                                                                                                                                                     
Get:57 http://ubuntuarchive.eweka.nl oneiric-security/restricted Translation-en [14 B]                                                                                                                                                        
Get:58 http://ubuntuarchive.eweka.nl oneiric-security/universe Translation-en [22.1 kB]                                                                                                                                                       
Fetched 16.8 MB in 20s (821 kB/s)                                                                                                                                                                                                             
Reading package lists... Done
carl@carl-Dell-DXC051:~$ 



```

I'm a bit stuck as to how to fix this, any advice would be most welcome :)

---

### Post by wildmanne39 on 2012-03-24
Hi, now run ```
sudo apt-get upgrade
```
and see if it completes because there is nothing wrong with the second information you posted.

---

### Post by CarlWalters on 2012-03-24
> **wildmanne39 said:**
> Hi, now run ```
sudo apt-get upgrade
```
and see if it completes because there is nothing wrong with the second information you posted.
thanks for the reply :)

The output of sudo apt-get upgrade is 

```

sudo apt-get upgrade
[sudo] password for carl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 libsclang1 : Depends: libscsynth1 but it is not installed
E: Unmet dependencies. Try using -f.
carl@carl-Dell-DXC051:~$ 

```

so I now run sudo apt-get -f upgrade and the output is 

```

carl@carl-Dell-DXC051:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed
  libscsynth1
The following packages have been kept back:
  gxtuner
The following packages will be upgraded:
  app-install-data-partner apt apt-transport-https apt-utils checkbox checkbox-gtk dssi-host-jack dssi-utils firefox firefox-globalmenu firefox-gnome-support firefox-locale-en flashplugin-downloader flashplugin-installer
  gstreamer0.10-gconf gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gzip handbrake-gtk hydrogen jackd2 jackd2-firewire language-pack-en language-pack-gnome-en libapt-inst1.3 libapt-pkg4.11 libc-bin libc-dev-bin libc6 libc6-dev
  libcec libfluidsynth1 libfreetype6 libjack-jackd2-0 liblightdm-gobject-1-0 libmysqlclient16 libnautilus-extension1 libpng12-0 libpng12-dev lightdm linux-headers-3.0.0-16 linux-headers-3.0.0-16-generic linux-image-3.0.0-16-generic
  linux-libc-dev multiarch-support mysql-common nautilus nautilus-data nuvolaplayer python-pam software-center supercollider-doc supercollider-server thunderbird thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-gb thunderbird-locale-en-us tzdata tzdata-java wine1.3 winetricks xbmc xbmc-bin xserver-xorg-video-openchrome xul-ext-ubufox
67 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 175 MB/176 MB of archives.
After this operation, 6,861 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libc-dev-bin i386 2.13-20ubuntu5.1 [77.5 kB]
Get:2 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main jackd2-firewire i386 1.9.8~dfsg.2-1oneiric1 [71.3 kB]
Get:3 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libc6-dev i386 2.13-20ubuntu5.1 [5,038 kB]
Get:4 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main jackd2 i386 1.9.8~dfsg.2-1oneiric1 [606 kB]
Get:5 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main libjack-jackd2-0 i386 1.9.8~dfsg.2-1oneiric1 [203 kB]
Get:6 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main supercollider-server i386 1:3.4.4-2ubuntu3~oneiric0 [538 kB]
Get:7 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ oneiric/main wine1.3 i386 1.4-0ubuntu1~ppa1~oneiric1 [13.2 MB]
Get:8 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libc-bin i386 2.13-20ubuntu5.1 [934 kB]                                                                                                                                      
Get:9 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libc6 i386 2.13-20ubuntu5.1 [3,800 kB]                                                                                                                                       
Get:10 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main linux-libc-dev i386 3.0.0-16.29 [831 kB]                                                                                                                                    
Get:11 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main tzdata-java i386 2012b-0ubuntu0.11.10 [134 kB]                                                                                                                              
Get:12 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main tzdata i386 2012b-0ubuntu0.11.10 [397 kB]                                                                                                                                   
Get:13 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main gzip i386 1.3.12-9ubuntu1.2 [74.4 kB]                                                                                                                                       
Get:14 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main language-pack-en all 1:11.10+20120306 [39.8 kB]                                                                                                                             
Get:15 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main language-pack-gnome-en all 1:11.10+20120306 [135 kB]                                                                                                                        
Get:16 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libfreetype6 i386 2.4.4-2ubuntu1.2 [338 kB]                                                                                                                                 
Get:17 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libpng12-dev i386 1.2.46-3ubuntu1.2 [207 kB]                                                                                                                                
Get:18 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libpng12-0 i386 1.2.46-3ubuntu1.2 [135 kB]                                                                                                                                  
Get:19 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main lightdm i386 1.0.6-0ubuntu1.6 [97.3 kB]                                                                                                                                     
Get:20 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main linux-image-3.0.0-16-generic i386 3.0.0-16.29 [36.5 MB]                                                                                                                     
Get:21 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ oneiric/main winetricks i386 0.0+20120308~ppa1 [147 kB]                                                                                                                               
Get:22 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main dssi-host-jack i386 1.1.1~dfsg0-1~oneiric1 [23.1 kB]                                                                                                                           
Get:23 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main dssi-utils i386 1.1.1~dfsg0-1~oneiric1 [22.5 kB]                                                                                                                               
Get:24 http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ oneiric/main handbrake-gtk i386 4531svnppa1~oneiric1 [7,121 kB]                                                                                                          
Get:25 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main hydrogen i386 0.9.6~beta1-1ubuntu1~oneiric1 [7,286 kB]                                                                                                                         
Get:26 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main libfluidsynth1 i386 1.1.5-20120312~oneiric1 [160 kB]                                                                                                                           
Get:27 http://ppa.launchpad.net/nuvola-player-builders/stable/ubuntu/ oneiric/main nuvolaplayer i386 1.0.3-0ubuntu0fenryxo1~oneiric [194 kB]                                                                                                  
Get:28 http://ppa.launchpad.net/dns/sound/ubuntu/ oneiric/main supercollider-doc all 1:3.4.4-2ubuntu3~oneiric0 [1,587 kB]                                                                                                                     
Get:29 http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu/ oneiric/main xbmc all 2:11.0~rc2-0~ppa1~oneiric [22.3 MB]                                                                                                            
Get:30 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libapt-pkg4.11 i386 0.8.16~exp5ubuntu13.2 [522 kB]                                                                                                                          
Get:31 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main apt i386 0.8.16~exp5ubuntu13.2 [1,046 kB]                                                                                                                                   
Get:32 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main multiarch-support i386 2.13-20ubuntu5.1 [4,476 B]                                                                                                                           
Get:33 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libapt-inst1.3 i386 0.8.16~exp5ubuntu13.2 [37.4 kB]                                                                                                                         
Get:34 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main apt-utils i386 0.8.16~exp5ubuntu13.2 [190 kB]                                                                                                                               
Get:35 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main app-install-data-partner all 12.11.10.2 [18.2 kB]                                                                                                                           
Get:36 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main apt-transport-https i386 0.8.16~exp5ubuntu13.2 [15.7 kB]                                                                                                                    
Get:37 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main checkbox-gtk all 0.12.10 [20.5 kB]                                                                                                                                          
Get:38 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main checkbox i386 0.12.10 [1,392 kB]                                                                                                                                            
Get:39 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main firefox-globalmenu i386 11.0+build1-0ubuntu0.11.10.1 [47.3 kB]                                                                                                              
Get:40 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main firefox i386 11.0+build1-0ubuntu0.11.10.1 [19.0 MB]                                                                                                                         
Get:41 http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu/ oneiric/main xbmc-bin i386 2:11.0~rc2-0~ppa1~oneiric [10.5 MB]                                                                                                       
Get:42 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main firefox-gnome-support i386 11.0+build1-0ubuntu0.11.10.1 [9,284 B]                                                                                                           
Get:43 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main firefox-locale-en all 11.0+build1-0ubuntu0.11.10.1 [419 kB]                                                                                                                 
Get:44 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/multiverse flashplugin-installer i386 11.1.102.63ubuntu0.11.10.1 [9,536 B]                                                                                                       
Get:45 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/multiverse flashplugin-downloader i386 11.1.102.63ubuntu0.11.10.1 [1,824 B]                                                                                                      
Get:46 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main gstreamer0.10-gconf i386 0.10.30-1ubuntu7.1 [63.9 kB]                                                                                                                       
Get:47 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main gstreamer0.10-plugins-good i386 0.10.30-1ubuntu7.1 [1,933 kB]                                                                                                               
Get:48 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main gstreamer0.10-pulseaudio i386 0.10.30-1ubuntu7.1 [90.0 kB]                                                                                                                  
Get:49 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main liblightdm-gobject-1-0 i386 1.0.6-0ubuntu1.6 [30.9 kB]                                                                                                                      
Get:50 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main mysql-common all 5.1.61-0ubuntu0.11.10.1 [11.8 kB]                                                                                                                          
Get:51 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libmysqlclient16 i386 5.1.61-0ubuntu0.11.10.1 [1,808 kB]                                                                                                                    
Get:52 http://ppa.launchpad.net/nathan-renniewaldock/xbmc-stable/ubuntu/ oneiric/main libcec i386 1.5.1-0~ppa1~oneiric [190 kB]                                                                                                               
Get:53 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main libnautilus-extension1 i386 1:3.2.1-0ubuntu4.2 [51.0 kB]                                                                                                                    
Get:54 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main linux-headers-3.0.0-16 all 3.0.0-16.29 [11.2 MB]                                                                                                                            
Get:55 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main linux-headers-3.0.0-16-generic i386 3.0.0-16.29 [855 kB]                                                                                                                    
Get:56 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main nautilus-data all 1:3.2.1-0ubuntu4.2 [71.8 kB]                                                                                                                              
Get:57 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main nautilus i386 1:3.2.1-0ubuntu4.2 [821 kB]                                                                                                                                   
Get:58 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main python-pam i386 0.4.2-12.2ubuntu2.11.10.1 [11.9 kB]                                                                                                                         
Get:59 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main software-center all 5.0.6 [697 kB]                                                                                                                                          
Get:60 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main thunderbird-globalmenu i386 11.0+build1-0ubuntu0.11.10.1 [47.1 kB]                                                                                                          
Get:61 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main thunderbird i386 11.0+build1-0ubuntu0.11.10.1 [21.5 MB]                                                                                                                     
Get:62 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main thunderbird-gnome-support i386 11.0+build1-0ubuntu0.11.10.1 [9,216 B]                                                                                                       
Get:63 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main thunderbird-locale-en all 1:11.0+build1-0ubuntu0.11.10.1 [345 kB]                                                                                                           
Get:64 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main thunderbird-locale-en-gb all 1:11.0+build1-0ubuntu0.11.10.1 [13.9 kB]                                                                                                       
Get:65 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main thunderbird-locale-en-us all 1:11.0+build1-0ubuntu0.11.10.1 [13.9 kB]                                                                                                       
Get:66 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main xserver-xorg-video-openchrome i386 1:0.2.904+svn920-1ubuntu0.2 [180 kB]                                                                                                     
Get:67 http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates/main xul-ext-ubufox all 1.0.3-0ubuntu1 [47.0 kB]                                                                                                                                 
Fetched 175 MB in 2min 7s (1,374 kB/s)                                                                                                                                                                                                        
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 294708 files and directories currently installed.)
Preparing to replace libc-dev-bin 2.13-20ubuntu5 (using .../libc-dev-bin_2.13-20ubuntu5.1_i386.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.13-20ubuntu5 (using .../libc6-dev_2.13-20ubuntu5.1_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc-bin 2.13-20ubuntu5 (using .../libc-bin_2.13-20ubuntu5.1_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.13-20ubuntu5.1) ...
(Reading database ... 294708 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu5 (using .../libc6_2.13-20ubuntu5.1_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.13-20ubuntu5.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 294708 files and directories currently installed.)
Preparing to replace linux-libc-dev 3.0.0-16.28 (using .../linux-libc-dev_3.0.0-16.29_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace tzdata-java 2011n-0ubuntu0.11.10 (using .../tzdata-java_2012b-0ubuntu0.11.10_i386.deb) ...
Unpacking replacement tzdata-java ...
Preparing to replace tzdata 2011n-0ubuntu0.11.10 (using .../tzdata_2012b-0ubuntu0.11.10_i386.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2012b-0ubuntu0.11.10) ...

Current default time zone: 'Europe/London'
Local time is now:      Sat Mar 24 16:50:31 GMT 2012.
Universal Time is now:  Sat Mar 24 16:50:31 UTC 2012.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 294712 files and directories currently installed.)
Preparing to replace jackd2-firewire 1.9.8~dfsg.1-1ubuntu1~oneiric0 (using .../jackd2-firewire_1.9.8~dfsg.2-1oneiric1_i386.deb) ...
Unpacking replacement jackd2-firewire ...
dpkg: libjack-jackd2-0: dependency problems, but removing anyway as you requested:
 lmms depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 gstreamer0.10-plugins-good depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 mplayer depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 supercollider-server depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 sooperlooper depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 qjackctl depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 gxtuner depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 audacious-plugins depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 hydrogen depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 libavdevice53 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 rakarrack depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 libportaudio2 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 libasound2-plugins depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 librtaudio4 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 libfluidsynth1 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 jackd2 depends on libjack-jackd2-0 (= 1.9.8~dfsg.1-1ubuntu1~oneiric0).
 dssi-host-jack depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 avidemux-plugins-common depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 librtmidi1 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 ams depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 lmms depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 gstreamer0.10-plugins-good depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 mplayer depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 supercollider-server depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 sooperlooper depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 qjackctl depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 gxtuner depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 audacious-plugins depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 hydrogen depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 libavdevice53 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 rakarrack depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 libportaudio2 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 libasound2-plugins depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 librtaudio4 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 libfluidsynth1 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 dssi-host-jack depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 avidemux-plugins-common depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 librtmidi1 depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
 ams depends on libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116; however:
  Package libjack-jackd2-0 is to be removed.
  Package libjack-0.116 is not installed.
  Package libjack-jackd2-0 which provides libjack-0.116 is to be removed.
(Reading database ... 294712 files and directories currently installed.)
Removing libjack-jackd2-0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 294702 files and directories currently installed.)
Preparing to replace jackd2 1.9.8~dfsg.1-1ubuntu1~oneiric0 (using .../jackd2_1.9.8~dfsg.2-1oneiric1_i386.deb) ...
Unpacking replacement jackd2 ...
Selecting previously deselected package libjack-jackd2-0.
Unpacking libjack-jackd2-0 (from .../libjack-jackd2-0_1.9.8~dfsg.2-1oneiric1_i386.deb) ...
Unpacking libscsynth1 (from .../libscsynth1_1%3a3.4.4-2ubuntu3~oneiric0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libscsynth1_1%3a3.4.4-2ubuntu3~oneiric0_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libscsynth.so.1', which is also in package supercollider-server 1:3.4.4-0ubuntu2~oneiric3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace supercollider-server 1:3.4.4-0ubuntu2~oneiric3 (using .../supercollider-server_1%3a3.4.4-2ubuntu3~oneiric0_i386.deb) ...
Unpacking replacement supercollider-server ...
Preparing to replace gzip 1.3.12-9ubuntu1.1 (using .../gzip_1.3.12-9ubuntu1.2_i386.deb) ...
Unpacking replacement gzip ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Errors were encountered while processing:
 /var/cache/apt/archives/libscsynth1_1%3a3.4.4-2ubuntu3~oneiric0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by CarlWalters on 2012-03-24
well the above followed by sudo apt-get update seems to have done the trick and all now seems fine.  Many thanks :)

---

### Post by wildmanne39 on 2012-03-24
Hi, your welcome! please use thread tools at the top of the page to mark thread solved.
Thanks

---

### Post by dparla on 2012-03-25
Had same problem but fixed with above! Thanks

---

