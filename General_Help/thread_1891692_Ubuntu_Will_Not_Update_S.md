---
title: "Ubuntu Will Not Update :S"
date: 2011-12-06
forum: General Help
---

### Post by xoron on 2011-12-06
Ubuntu Will Not Update :S

well basically it will not update... nothings comes up on the update manager and when i sudo apt-get update, it gives an error.

```


Ign http://gb.archive.ubuntu.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                 
Ign http://gb.archive.ubuntu.com oneiric-backports InRelease               
Ign http://security.ubuntu.com oneiric-security InRelease                  
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                  
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                 
Get:2 http://gb.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg       
Hit http://security.ubuntu.com oneiric-security Release              
Hit http://gb.archive.ubuntu.com oneiric Release                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                        
Get:3 http://gb.archive.ubuntu.com oneiric-updates Release [32.4 kB]  
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Get:4 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://gb.archive.ubuntu.com oneiric-backports Release                     
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://gb.archive.ubuntu.com oneiric/main Sources                          
Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://gb.archive.ubuntu.com oneiric/universe Sources                      
Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:5 http://gb.archive.ubuntu.com oneiric-updates/main Sources [94.3 kB]      
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Ign http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources        
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Get:6 http://gb.archive.ubuntu.com oneiric-updates/restricted Sources [1,348 B]
Get:7 http://gb.archive.ubuntu.com oneiric-updates/universe Sources [25.8 kB]  
Get:8 http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources [1,992 B]
Get:9 http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages [219 kB] 
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources                             
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                       
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Get:10 http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,935 B]
Get:11 http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages [64.1 kB]
Get:12 http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [4,396 B]
Get:13 http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]
Get:14 http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:15 http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:16 http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://gb.archive.ubuntu.com oneiric-backports/main Sources
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en
Hit http://gb.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en
Fetched 447 kB in 0s (1,268 kB/s)
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2E3912DEB33004BC
W: Failed to fetch http://ppa.launchpad.net/gijzelaar/opencv2/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gijzelaar/opencv2/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by plucky on 2011-12-06
[http://ppa.launchpad.net/gijzelaar/opencv2/ubuntu/dists/](http://ppa.launchpad.net/gijzelaar/opencv2/ubuntu/dists/)
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/)

There is no PPA's for oneiric in the lines that giving the 404 error.

Open Software Sources and delete the ones that are causing the problem,then try to update again.

Good Luck

---

