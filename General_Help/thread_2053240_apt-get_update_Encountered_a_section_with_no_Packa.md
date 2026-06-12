---
title: "apt-get update: Encountered a section with no Package: header"
date: 2012-09-04
forum: General Help
---

### Post by sebin on 2012-09-04
I am receiving this error

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```

I have seen this post[HTML]http://ubuntuforums.org/showthread.php?t=2026749[/HTML]

I don't think, my issue is Synaptic.

---

### Post by sebin on 2012-09-04
here is my output

```
seb@seb-desk:~$ sudo apt-get clean 
[sudo] password for seb: 
seb@seb-desk:~$ sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://in.archive.ubuntu.com precise InRelease                             
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease                   
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://in.archive.ubuntu.com precise Release.gpg                           
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://archive.canonical.com precise Release                               
Get:3 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://in.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://in.archive.ubuntu.com precise Release                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:4 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://ppa.launchpad.net precise Release                                   
Get:5 http://security.ubuntu.com precise-security/main Sources [41.4 kB]       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://in.archive.ubuntu.com precise-backports Release                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:6 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:7 http://security.ubuntu.com precise-security/universe Sources [12.2 kB]   
Get:8 http://security.ubuntu.com precise-security/multiverse Sources [1,386 B] 
Get:9 http://security.ubuntu.com precise-security/main i386 Packages [163 kB]  
Hit http://in.archive.ubuntu.com precise/main Sources                          
Hit http://in.archive.ubuntu.com precise/restricted Sources                    
Hit http://in.archive.ubuntu.com precise/universe Sources                      
Hit http://in.archive.ubuntu.com precise/multiverse Sources                    
Hit http://in.archive.ubuntu.com precise/main i386 Packages                    
Hit http://in.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://in.archive.ubuntu.com precise/universe i386 Packages                
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://in.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://in.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex             
Get:10 http://in.archive.ubuntu.com precise-updates/main Sources [159 kB]      
Get:11 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:12 http://in.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [41.6 kB]
Get:14 http://in.archive.ubuntu.com precise-updates/universe Sources [50.1 kB] 
Get:15 http://in.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:16 http://in.archive.ubuntu.com precise-updates/main i386 Packages [381 kB]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://archive.canonical.com precise/partner Translation-en_IN             
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_IN
Ign http://ppa.launchpad.net precise/main Translation-en 
Ign http://ppa.launchpad.net precise/main Translation-en_IN
Ign http://ppa.launchpad.net precise/main Translation-en 
Ign http://ppa.launchpad.net precise/main Translation-en_IN
Ign http://ppa.launchpad.net precise/main Translation-en 
Ign http://ppa.launchpad.net precise/main Translation-en_IN
Ign http://ppa.launchpad.net precise/main Translation-en
Get:18 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:19 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [127 kB]
Get:20 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://in.archive.ubuntu.com precise-backports/main Sources                
Hit http://in.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://in.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://in.archive.ubuntu.com precise-backports/universe Sources            
Hit http://in.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://in.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://in.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://in.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://in.archive.ubuntu.com precise/main Translation-en                   
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://in.archive.ubuntu.com precise/restricted Translation-en             
Hit http://in.archive.ubuntu.com precise/universe Translation-en               
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://in.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://in.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://in.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://in.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 1,108 kB in 7s (143 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```

---

### Post by cortman on 2012-09-04
Hi, run

```
sudo rm  /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
sudo apt-get update
```

and see if that fixes it.

---

### Post by sebin on 2012-09-05
Hope this error is different and normal 
 
```
seb@seb-desk:~$ sudo rm  /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
[sudo] password for seb: 
seb@seb-desk:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise InRelease                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                       
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [12.0 kB]                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release                     
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [22.6 kB]            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex             
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [159 kB]       
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Sources [50.1 kB]  
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main i386 Packages [381 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe i386 Packages [127 kB]
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Translation-en             
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Translation-en [3,341 kB] 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_IN             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]         
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [41.4 kB]      
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [12.2 kB]  
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [163 kB] 
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [41.6 kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [184 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Translation-en                                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Translation-en                                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Translation-en                                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources/DiffIndex                                                                                                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex                                                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                                                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                                                                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN                                                                                                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                                                                       
Fetched 4,691 kB in 48s (95.9 kB/s)                                                                                                                                            
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
E: Some index files failed to download. They have been ignored, or old ones used instead.
seb@seb-desk:~$ 

```

---

### Post by sebin on 2012-09-05
I am having another issue. i have posted this in another thread
[http://ubuntuforums.org/showthread.php?p=12218889#post12218889](http://ubuntuforums.org/showthread.php?p=12218889#post12218889)

Hope both are not connected.

---

### Post by cortman on 2012-09-05
Your mirrors are probably not optimally set. Go to the gear icon in the upper right, select "Software Updater", press the settings button, and under the first tab (Ubuntu Software) change the "Download from:" to a mirror nearer to you (you can use the "select best server" button to accomplish this.

---

### Post by sebin on 2012-09-05
Thank you. this issue is sorted out.. thank you

---

