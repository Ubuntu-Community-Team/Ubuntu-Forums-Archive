---
title: "install adobe acrobat reader for firefox plug-in"
date: 2012-01-11
forum: General Help
---

### Post by ainshtin on 2012-01-11
I tried to install adobe acrobat reader for firefox plug-in, so I used

sudo add-apt-repository "deb deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free"  && sudo apt-get update 
[FONT=Georgia]sudo apt-get install acroread mozilla-acroread acroread-plugins acroread-fonts

but first give this:
[/FONT]
:~$ sudo add-apt-repository "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free"  && sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease [7,092 B]                  
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty InRelease                               
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:3 [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Sources/DiffIndex                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates Release                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Sources/DiffIndex             
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/main Sources                            
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/universe Sources                        
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/main TranslationIndex                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages/DiffIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/universe TranslationIndex               
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [1,338 B]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages/DiffIndex       
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Get:7 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [464 B]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) natty-updates/universe Translation-en         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Sources                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en
Fetched 2,831 B in 17s (160 B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://ppa.launchpad.net/Ubuntu-wine/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/Ubuntu-wine/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/Ubuntu-wine/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/Ubuntu-wine/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.







any ideas ??

- thx in advance -

---

### Post by bluexrider on 2012-01-11
> **ainshtin said:**
> 


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Failed to fetch [http://ppa.launchpad.net/Ubuntu-wine/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/Ubuntu-wine/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/Ubuntu-wine/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/Ubuntu-wine/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.



Need to import the GPG key for Medibuntu

Run this in terminal

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```


and need to edit the sources.list file for the other issue

please post output of this 

```
cat /etc/apt/sources.list

```

---

