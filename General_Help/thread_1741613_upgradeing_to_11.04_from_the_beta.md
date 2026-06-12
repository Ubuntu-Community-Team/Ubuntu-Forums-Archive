---
title: "upgradeing to 11.04 from the beta"
date: 2011-04-28
forum: General Help
---

### Post by Reduced_Oxygen on 2011-04-28
how?

when ever i hit check in updates it tells me to check my connection, i have changed sources several times

---

### Post by Elfy on 2011-04-28
It might be just that everyone is hitting the servers at the same time.

If it's not that please run sudo apt-get update and post the error.

(As an aside I always leave the servers well alone on release day.)

---

### Post by Reduced_Oxygen on 2011-04-28
> **forestpiskie said:**
> It might be just that everyone is hitting the servers at the same time.

If it's not that please run sudo apt-get update and post the error.

(As an aside I always leave the servers well alone on release day.)
your probably right but heres the errors anyways thanks:
```
gilligan@Gilligan-Desktop:~$ sudo apt-get update
[sudo] password for gilligan: 
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty/restricted TranslationIndex
Err cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1) natty/restricted Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Ign http://mirror.netspace.net.au natty InRelease                              
Ign http://mirror.netspace.net.au natty-updates InRelease                      
Ign http://mirror.netspace.net.au natty-security InRelease                     
Hit http://mirror.netspace.net.au natty Release.gpg                            
Hit http://mirror.netspace.net.au natty-updates Release.gpg                    
Hit http://mirror.netspace.net.au natty-security Release.gpg                   
Hit http://mirror.netspace.net.au natty Release                                
Hit http://mirror.netspace.net.au natty-updates Release                        
Hit http://mirror.netspace.net.au natty-security Release                       
Hit http://mirror.netspace.net.au natty/main Sources                           
Hit http://mirror.netspace.net.au natty/restricted Sources                     
Hit http://mirror.netspace.net.au natty/universe Sources                       
Hit http://mirror.netspace.net.au natty/multiverse Sources                     
Hit http://mirror.netspace.net.au natty/main i386 Packages                     
Hit http://mirror.netspace.net.au natty/restricted i386 Packages               
Hit http://mirror.netspace.net.au natty/universe i386 Packages                 
Hit http://mirror.netspace.net.au natty/multiverse i386 Packages               
Ign http://mirror.netspace.net.au natty/main TranslationIndex                  
Ign http://mirror.netspace.net.au natty/multiverse TranslationIndex            
Ign http://mirror.netspace.net.au natty/restricted TranslationIndex            
Ign http://mirror.netspace.net.au natty/universe TranslationIndex              
Hit http://mirror.netspace.net.au natty-updates/main Sources                   
Hit http://mirror.netspace.net.au natty-updates/restricted Sources             
Hit http://mirror.netspace.net.au natty-updates/universe Sources               
Hit http://mirror.netspace.net.au natty-updates/multiverse Sources             
Hit http://mirror.netspace.net.au natty-updates/main i386 Packages             
Hit http://mirror.netspace.net.au natty-updates/restricted i386 Packages       
Hit http://mirror.netspace.net.au natty-updates/universe i386 Packages         
Hit http://mirror.netspace.net.au natty-updates/multiverse i386 Packages       
Ign http://mirror.netspace.net.au natty-updates/main TranslationIndex          
Ign http://mirror.netspace.net.au natty-updates/multiverse TranslationIndex    
Ign http://mirror.netspace.net.au natty-updates/restricted TranslationIndex    
Ign http://mirror.netspace.net.au natty-updates/universe TranslationIndex      
Hit http://mirror.netspace.net.au natty-security/main Sources                  
Hit http://mirror.netspace.net.au natty-security/restricted Sources            
Hit http://mirror.netspace.net.au natty-security/universe Sources              
Hit http://mirror.netspace.net.au natty-security/multiverse Sources            
Hit http://mirror.netspace.net.au natty-security/main i386 Packages            
Hit http://mirror.netspace.net.au natty-security/restricted i386 Packages      
Hit http://mirror.netspace.net.au natty-security/universe i386 Packages        
Hit http://mirror.netspace.net.au natty-security/multiverse i386 Packages      
Ign http://mirror.netspace.net.au natty-security/main TranslationIndex         
Ign http://mirror.netspace.net.au natty-security/multiverse TranslationIndex   
Ign http://mirror.netspace.net.au natty-security/restricted TranslationIndex   
Ign http://mirror.netspace.net.au natty-security/universe TranslationIndex     
Ign http://ppa.launchpad.net maverick InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://mirror.netspace.net.au natty/main Translation-en_US                 
Ign http://mirror.netspace.net.au natty/main Translation-en                    
Ign http://mirror.netspace.net.au natty/multiverse Translation-en_US           
Ign http://mirror.netspace.net.au natty/multiverse Translation-en              
Ign http://mirror.netspace.net.au natty/restricted Translation-en_US           
Ign http://mirror.netspace.net.au natty/restricted Translation-en              
Ign http://mirror.netspace.net.au natty/universe Translation-en_US             
Ign http://mirror.netspace.net.au natty/universe Translation-en                
Ign http://mirror.netspace.net.au natty-updates/main Translation-en_US         
Ign http://mirror.netspace.net.au natty-updates/main Translation-en            
Ign http://mirror.netspace.net.au natty-updates/multiverse Translation-en_US   
Ign http://mirror.netspace.net.au natty-updates/multiverse Translation-en      
Ign http://mirror.netspace.net.au natty-updates/restricted Translation-en_US   
Ign http://mirror.netspace.net.au natty-updates/restricted Translation-en      
Ign http://mirror.netspace.net.au natty-updates/universe Translation-en_US     
Ign http://mirror.netspace.net.au natty-updates/universe Translation-en        
Ign http://mirror.netspace.net.au natty-security/main Translation-en_US        
Ign http://mirror.netspace.net.au natty-security/main Translation-en           
Ign http://mirror.netspace.net.au natty-security/multiverse Translation-en_US  
Ign http://mirror.netspace.net.au natty-security/multiverse Translation-en     
Ign http://mirror.netspace.net.au natty-security/restricted Translation-en_US  
Ign http://mirror.netspace.net.au natty-security/restricted Translation-en     
Ign http://mirror.netspace.net.au natty-security/universe Translation-en_US    
Ign http://mirror.netspace.net.au natty-security/universe Translation-en       
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                    
Hit http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Hit http://ppa.launchpad.net natty/main Sources                               
Hit http://ppa.launchpad.net natty/main i386 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Ign http://extras.ubuntu.com natty InRelease                                  
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Hit http://ppa.launchpad.net natty/main Sources                               
Hit http://ppa.launchpad.net natty/main i386 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Hit http://ppa.launchpad.net natty/main Sources                               
Hit http://ppa.launchpad.net natty/main i386 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://extras.ubuntu.com natty Release.gpg                                 
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Hit http://ppa.launchpad.net natty/main Sources                               
Hit http://extras.ubuntu.com natty Release                                     
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Hit http://extras.ubuntu.com natty/main Sources                                
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                         
  404  Not Found
Err http://ppa.launchpad.net natty/main Sources                               
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                         
  404  Not Found
Err http://ppa.launchpad.net natty/main Sources         
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages   
  404  Not Found
Err http://ppa.launchpad.net natty/main Sources         
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages   
  404  Not Found
Err http://ppa.launchpad.net natty/main Sources         
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages   
  404  Not Found
Ign http://ppa.launchpad.net maverick/main Translation-en_US                  
Ign http://ppa.launchpad.net maverick/main Translation-en                     
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://ppa.launchpad.net natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en  
Err http://archive.canonical.com natty InRelease        
  
Err http://archive.canonical.com natty Release.gpg      
  Unable to connect to archive.canonical.com:http:
Reading package lists... Done
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/https/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/https/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ppa/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ppa/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to archive.canonical.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Elfy on 2011-04-28
You need to disable those ppa's unless there's actually a natty one.

I'd also disable the cdrom unless it's in the machine and you want to use it.

---

### Post by Elfy on 2011-04-28
You need to disable those ppa's unless there's actually a natty one.

I'd also disable the cdrom unless it's in the machine and you want to use it.

---

### Post by Reduced_Oxygen on 2011-05-04
> **forestpiskie said:**
> You need to disable those ppa's unless there's actually a natty one.

I'd also disable the cdrom unless it's in the machine and you want to use it.
thank you

---

