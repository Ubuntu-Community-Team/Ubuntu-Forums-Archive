---
title: "Problems with sources.lists"
date: 2012-01-08
forum: General Help
---

### Post by Dadof4 on 2012-01-08
Again I am having errors showing after I update. They had cleared for about 3 days and then I tried to install Medibuntu and all heck broke lose. I really want to get this fixed and then see if someone can tell me what I did wrong. After I tried the Meidbuntu I tried to install Playonlinux and the Fix404 (not the brightest idea I've ever had). The wine/playonlinux is an irritating animal in it's own right and I need to address that in another post.

This is the output I get when I run ```
sudo apt-get update
```

```
Ign http://mirror.anl.gov oneiric InRelease
Ign http://mirror.anl.gov oneiric-updates InRelease                            
Ign http://mirror.anl.gov oneiric-security InRelease                           
Ign http://mirror.anl.gov oneiric-proposed InRelease                           
Ign http://mirror.anl.gov oneiric-backports InRelease                          
Hit http://mirror.anl.gov oneiric Release.gpg                                  
Ign http://dl.google.com stable InRelease                                      
Hit http://mirror.anl.gov oneiric-updates Release.gpg                          
Hit http://mirror.anl.gov oneiric-security Release.gpg                         
Hit http://mirror.anl.gov oneiric-proposed Release.gpg                         
Ign http://dl.google.com stable InRelease                                      
Hit http://mirror.anl.gov oneiric-backports Release.gpg                        
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://mirror.anl.gov oneiric Release                                      
Hit http://mirror.anl.gov oneiric-updates Release                              
Hit http://mirror.anl.gov oneiric-security Release                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://mirror.anl.gov oneiric-proposed Release                             
Ign http://deb.playonlinux.com oneiric InRelease                               
Ign http://archive.canonical.com oneiric InRelease                             
Hit http://packages.medibuntu.org natty InRelease                              
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://mirror.anl.gov oneiric-backports Release                            
Hit http://mirror.anl.gov oneiric/restricted Sources                           
Hit http://mirror.anl.gov oneiric/main Sources                                 
Hit http://mirror.anl.gov oneiric/multiverse Sources                           
Hit http://mirror.anl.gov oneiric/universe Sources                             
Hit http://mirror.anl.gov oneiric/main amd64 Packages                          
Hit http://mirror.anl.gov oneiric/restricted amd64 Packages                    
Hit http://mirror.anl.gov oneiric/universe amd64 Packages                      
Hit http://mirror.anl.gov oneiric/multiverse amd64 Packages                    
Hit http://mirror.anl.gov oneiric/main i386 Packages                           
Hit http://mirror.anl.gov oneiric/restricted i386 Packages                     
Hit http://mirror.anl.gov oneiric/universe i386 Packages                       
Hit http://mirror.anl.gov oneiric/multiverse i386 Packages                     
Hit http://mirror.anl.gov oneiric/main TranslationIndex                        
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://mirror.anl.gov oneiric/multiverse TranslationIndex                  
Hit http://mirror.anl.gov oneiric/restricted TranslationIndex                  
Hit http://mirror.anl.gov oneiric/universe TranslationIndex                    
Hit http://mirror.anl.gov oneiric-updates/restricted Sources                   
Hit http://mirror.anl.gov oneiric-updates/main Sources                         
Hit http://mirror.anl.gov oneiric-updates/multiverse Sources                   
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://archive.getdeb.net jaunty-getdeb InRelease                          
Ign http://archive.getdeb.net oneiric-getdeb InRelease                         
Hit http://mirror.anl.gov oneiric-updates/universe Sources                     
Hit http://mirror.anl.gov oneiric-updates/main amd64 Packages                  
Hit http://mirror.anl.gov oneiric-updates/restricted amd64 Packages            
Hit http://mirror.anl.gov oneiric-updates/universe amd64 Packages              
Hit http://mirror.anl.gov oneiric-updates/multiverse amd64 Packages            
Hit http://mirror.anl.gov oneiric-updates/main i386 Packages                   
Hit http://mirror.anl.gov oneiric-updates/restricted i386 Packages             
Hit http://mirror.anl.gov oneiric-updates/universe i386 Packages               
Hit http://mirror.anl.gov oneiric-updates/multiverse i386 Packages             
Hit http://mirror.anl.gov oneiric-updates/main TranslationIndex                
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://deb.playonlinux.com oneiric Release.gpg                             
Hit http://mirror.anl.gov oneiric-updates/multiverse TranslationIndex          
Hit http://mirror.anl.gov oneiric-updates/restricted TranslationIndex          
Hit http://mirror.anl.gov oneiric-updates/universe TranslationIndex            
Hit http://mirror.anl.gov oneiric-security/restricted Sources                  
Hit http://mirror.anl.gov oneiric-security/main Sources                        
Hit http://archive.canonical.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://mirror.anl.gov oneiric-security/multiverse Sources                  
Hit http://mirror.anl.gov oneiric-security/universe Sources                    
Hit http://mirror.anl.gov oneiric-security/main amd64 Packages                 
Hit http://mirror.anl.gov oneiric-security/restricted amd64 Packages           
Hit http://mirror.anl.gov oneiric-security/universe amd64 Packages             
Hit http://packages.medibuntu.org oneiric InRelease                            
Hit http://mirror.anl.gov oneiric-security/multiverse amd64 Packages           
Hit http://mirror.anl.gov oneiric-security/main i386 Packages                  
Hit http://mirror.anl.gov oneiric-security/restricted i386 Packages            
Hit http://mirror.anl.gov oneiric-security/universe i386 Packages              
Hit http://mirror.anl.gov oneiric-security/multiverse i386 Packages            
Hit http://deb.playonlinux.com oneiric Release                                 
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://mirror.anl.gov oneiric-security/main TranslationIndex               
Hit http://mirror.anl.gov oneiric-security/multiverse TranslationIndex         
Hit http://mirror.anl.gov oneiric-security/restricted TranslationIndex         
Hit http://mirror.anl.gov oneiric-security/universe TranslationIndex           
Hit http://mirror.anl.gov oneiric-proposed/restricted Sources                  
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://mirror.anl.gov oneiric-proposed/main Sources                        
Hit http://mirror.anl.gov oneiric-proposed/multiverse Sources                  
Hit http://mirror.anl.gov oneiric-proposed/universe Sources                    
Hit http://mirror.anl.gov oneiric-proposed/restricted amd64 Packages           
Hit http://mirror.anl.gov oneiric-proposed/main amd64 Packages                 
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://mirror.anl.gov oneiric-proposed/multiverse amd64 Packages           
Hit http://mirror.anl.gov oneiric-proposed/universe amd64 Packages             
Hit http://mirror.anl.gov oneiric-proposed/restricted i386 Packages            
Hit http://mirror.anl.gov oneiric-proposed/main i386 Packages                  
Hit http://mirror.anl.gov oneiric-proposed/multiverse i386 Packages            
Get:3 http://dl.google.com stable Release [1,347 B]                            
Hit http://deb.playonlinux.com oneiric/main amd64 Packages                     
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://mirror.anl.gov oneiric-proposed/universe i386 Packages              
Hit http://mirror.anl.gov oneiric-proposed/main TranslationIndex               
Hit http://mirror.anl.gov oneiric-proposed/multiverse TranslationIndex         
Hit http://mirror.anl.gov oneiric-proposed/restricted TranslationIndex         
Hit http://mirror.anl.gov oneiric-proposed/universe TranslationIndex           
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://mirror.anl.gov oneiric-backports/restricted Sources                 
Hit http://mirror.anl.gov oneiric-backports/main Sources                       
Hit http://mirror.anl.gov oneiric-backports/multiverse Sources                 
Hit http://mirror.anl.gov oneiric-backports/universe Sources                   
Hit http://mirror.anl.gov oneiric-backports/restricted amd64 Packages          
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://mirror.anl.gov oneiric-backports/main amd64 Packages                
Hit http://mirror.anl.gov oneiric-backports/multiverse amd64 Packages          
Hit http://mirror.anl.gov oneiric-backports/universe amd64 Packages            
Hit http://mirror.anl.gov oneiric-backports/restricted i386 Packages           
Hit http://mirror.anl.gov oneiric-backports/main i386 Packages                 
Hit http://packages.medibuntu.org natty/free Sources                           
Hit http://deb.playonlinux.com oneiric/main i386 Packages                      
Ign http://deb.playonlinux.com oneiric/main TranslationIndex                   
Hit http://archive.getdeb.net jaunty-getdeb Release.gpg                        
Hit http://mirror.anl.gov oneiric-backports/multiverse i386 Packages           
Hit http://mirror.anl.gov oneiric-backports/universe i386 Packages             
Hit http://mirror.anl.gov oneiric-backports/main TranslationIndex              
Hit http://mirror.anl.gov oneiric-backports/multiverse TranslationIndex        
Hit http://mirror.anl.gov oneiric-backports/restricted TranslationIndex        
Get:4 http://dl.google.com stable Release [1,349 B]                            
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://mirror.anl.gov oneiric-backports/universe TranslationIndex          
Hit http://mirror.anl.gov oneiric/main Translation-en                          
Hit http://mirror.anl.gov oneiric/multiverse Translation-en                    
Hit http://mirror.anl.gov oneiric/restricted Translation-en                    
Hit http://mirror.anl.gov oneiric/universe Translation-en                      
Hit http://mirror.anl.gov oneiric-updates/main Translation-en                  
Hit http://mirror.anl.gov oneiric-updates/multiverse Translation-en            
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://mirror.anl.gov oneiric-updates/restricted Translation-en            
Hit http://mirror.anl.gov oneiric-updates/universe Translation-en              
Hit http://mirror.anl.gov oneiric-security/main Translation-en                 
Hit http://mirror.anl.gov oneiric-security/multiverse Translation-en           
Hit http://mirror.anl.gov oneiric-security/restricted Translation-en           
Hit http://mirror.anl.gov oneiric-security/universe Translation-en             
Hit http://mirror.anl.gov oneiric-proposed/main Translation-en                 
Hit http://mirror.anl.gov oneiric-proposed/multiverse Translation-en           
Hit http://mirror.anl.gov oneiric-proposed/restricted Translation-en           
Hit http://mirror.anl.gov oneiric-proposed/universe Translation-en             
Hit http://mirror.anl.gov oneiric-backports/main Translation-en                
Hit http://mirror.anl.gov oneiric-backports/multiverse Translation-en          
Hit http://packages.medibuntu.org natty/non-free Sources                       
Hit http://mirror.anl.gov oneiric-backports/restricted Translation-en          
Hit http://mirror.anl.gov oneiric-backports/universe Translation-en            
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.getdeb.net oneiric-getdeb Release.gpg                       
Hit http://packages.medibuntu.org natty/free amd64 Packages                    
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://packages.medibuntu.org natty/non-free amd64 Packages                
Hit http://archive.getdeb.net jaunty-getdeb Release                            
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://deb.playonlinux.com oneiric/main Translation-en_US                  
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://deb.playonlinux.com oneiric/main Translation-en                     
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Hit http://archive.getdeb.net oneiric-getdeb Release                           
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                       
  404  Not Found
Ign http://packages.medibuntu.org natty/free TranslationIndex        
Err http://ppa.launchpad.net oneiric/main i386 Packages              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                       
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages              
  404  Not Found
Ign http://packages.medibuntu.org natty/non-free TranslationIndex    
Ign http://ppa.launchpad.net oneiric/main Translation-en_US          
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:5 http://dl.google.com stable/main amd64 Packages [1,192 B]                
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://packages.medibuntu.org oneiric/free amd64 Packages              
Hit http://archive.getdeb.net jaunty-getdeb/games Sources                  
Hit http://archive.getdeb.net jaunty-getdeb/games amd64 Packages               
Hit http://archive.getdeb.net jaunty-getdeb/games i386 Packages                
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://archive.getdeb.net jaunty-getdeb/games TranslationIndex             
Hit http://packages.medibuntu.org oneiric/non-free amd64 Packages              
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages
Hit http://archive.getdeb.net oneiric-getdeb/games amd64 Packages
Hit http://archive.getdeb.net oneiric-getdeb/games i386 Packages               
Ign http://archive.getdeb.net oneiric-getdeb/games TranslationIndex            
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Get:6 http://dl.google.com stable/main i386 Packages [1,203 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Get:7 http://dl.google.com stable/main amd64 Packages [642 B]                  
Get:8 http://dl.google.com stable/main i386 Packages [641 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.getdeb.net jaunty-getdeb/games Translation-en_US            
Ign http://archive.getdeb.net jaunty-getdeb/games Translation-en               
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en_US           
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en              
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_US
Ign http://packages.medibuntu.org natty/non-free Translation-en
Ign http://packages.medibuntu.org oneiric/free Translation-en_US
Ign http://packages.medibuntu.org oneiric/free Translation-en
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_US
Ign http://packages.medibuntu.org oneiric/non-free Translation-en
Fetched 6,770 B in 17s (385 B/s)
W: Failed to fetch http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Sorry for the super long post this early in the morning but I figured it would be like a good cup of coffee! [-o<

---

### Post by CharlesA on 2012-01-08
You are getting 404 errors from a few of the ppas you have installed. Verify that those files exist and either update or remove the entry in sources.list

Check [here]("http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-using-a-ppa") too.

---

### Post by Frogs Hair on 2012-01-08
I noticed that the Medibuntu source is for Natty 11.04 and there is now an 11.10 only source .  [http://www.ubuntuvibes.com/2011/10/medibuntu-repository-now-available-for.html](http://www.ubuntuvibes.com/2011/10/medibuntu-repository-now-available-for.html)

---

### Post by oldos2er on 2012-01-08
Are you running 11.10? You really should remove all the repos that reference earlier versions.

Edit: Changed thread title.

---

