---
title: "Update manager and software center WON'T WORK"
date: 2011-06-29
forum: General Help
---

### Post by cheesekiller on 2011-06-29
The update manager gives me this error

```
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
```

I'm running 11.04 64bit

has anyone experienced this before?

I can't update or download software.

---

### Post by blueridgedog on 2011-06-29
Try:

```
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
sudo apt-get clean
sudo apt-get update
```

---

### Post by cheesekiller on 2011-06-29
```
sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Get:3 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.canonical.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Get:4 http://dl.google.com stable Release [1,351 B]                            
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://planet76.com ./ InRelease                                           
Ign http://security.ubuntu.com natty-security InRelease                        
Get:5 http://dl.google.com stable Release [1,338 B]                            
Get:6 http://archive.canonical.com natty Release.gpg [198 B]                   
Get:7 http://dl.google.com stable Release [1,347 B]                            
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Get:8 http://dl.google.com stable/main amd64 Packages [1,256 B]                
Get:9 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Hit http://security.ubuntu.com natty-security Release.gpg                      
Ign http://dl.google.com stable/main TranslationIndex                          
Get:10 http://dl.google.com stable/main amd64 Packages [469 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://planet76.com ./ Release.gpg                                         
Get:11 http://archive.canonical.com natty Release [5,916 B]                    
Get:12 http://dl.google.com stable/main amd64 Packages [757 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Get:13 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]          
Hit http://extras.ubuntu.com natty Release                                     
Hit http://security.ubuntu.com natty-security Release                          
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://planet76.com ./ Release                                             
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://security.ubuntu.com natty-security/main Sources                     
Get:14 http://archive.canonical.com natty/partner amd64 Packages [6,736 B]     
Ign http://archive.getdeb.net natty-getdeb InRelease                           
Get:15 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]            
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main amd64 Packages              
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages        
Hit http://planet76.com ./ Packages                                            
Hit http://security.ubuntu.com natty-security/universe amd64 Packages          
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages        
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main amd64 Packages                     
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages               
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Get:16 http://archive.getdeb.net natty-getdeb Release.gpg [836 B]              
Ign https://private-ppa.launchpad.net maverick InRelease                       
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Get:17 http://us.archive.ubuntu.com natty-updates/main Sources [89.1 kB]       
Get:18 http://archive.getdeb.net natty-getdeb Release [7,240 B]                
Get:19 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]    
Get:20 http://us.archive.ubuntu.com natty-updates/universe Sources [16.2 kB]   
Get:21 http://us.archive.ubuntu.com natty-updates/multiverse Sources [1,891 B] 
Get:22 http://us.archive.ubuntu.com natty-updates/main amd64 Packages [260 kB] 
Ign https://private-ppa.launchpad.net maverick InRelease                       
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://extras.ubuntu.com natty/main Translation-en                         
Get:23 http://archive.getdeb.net natty-getdeb/games amd64 Packages [59.0 kB]   
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Get:24 http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages [14 B]
Get:25 http://us.archive.ubuntu.com natty-updates/universe amd64 Packages [64.8 kB]
Ign http://planet76.com ./ Translation-en_US                                   
Get:26 https://private-ppa.launchpad.net maverick Release.gpg [316 B]          
Get:27 http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages [4,174 B]
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://planet76.com ./ Translation-en                                      
Get:28 https://private-ppa.launchpad.net maverick Release.gpg [316 B]          
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Hit https://private-ppa.launchpad.net maverick Release                         
Hit https://private-ppa.launchpad.net maverick Release                         
Hit https://private-ppa.launchpad.net maverick/main amd64 Packages             
Ign http://archive.getdeb.net natty-getdeb/games TranslationIndex              
Ign https://private-ppa.launchpad.net maverick/main TranslationIndex 
Hit https://private-ppa.launchpad.net maverick/main amd64 Packages             
Ign https://private-ppa.launchpad.net maverick/main TranslationIndex           
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                       
Ign http://dl.google.com stable/main Translation-en                          
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en                
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.getdeb.net natty-getdeb/games Translation-en_US             
Ign http://archive.getdeb.net natty-getdeb/games Translation-en                
Ign https://private-ppa.launchpad.net maverick/main Translation-en_US          
Ign https://private-ppa.launchpad.net maverick/main Translation-en
Ign https://private-ppa.launchpad.net maverick/main Translation-en_US
Ign https://private-ppa.launchpad.net maverick/main Translation-en
Fetched 552 kB in 16s (34.3 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.

```
I copy and pasted everything you wrote...
its still broken :(

---

### Post by blueridgedog on 2011-06-29
OK, lets just remove them all and then rebuild:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
```

---

### Post by cheesekiller on 2011-06-29
that fixed it now everything works....   what caused that?  do you know?  is there a way to prevent it from ever happening again?

Also your awesome thank you so much!

---

### Post by blueridgedog on 2011-06-30
I think it was a corrupt application list, probably due to a random drive sector flakiness or a crash when updating.  Good luck.

---

