---
title: "Ubuntu Software Center and such"
date: 2011-05-31
forum: General Help
---

### Post by The Eight-Bit Link on 2011-05-31
I have been having a mistrusted package problem with my package managers (Synaptic, USC, ect.) Whenever I attempt to install something, USC usually starts to load after auth, then pops up saying something about a failed download due to bad net, then I get an uncheckable package error. Is there something I can do about this? I can only install things via Synaptic, and it isn't as 'friendly' as USC.

Thanks to the kind being who solves and/or explains this in advance.

---

### Post by plucky on 2011-06-01
> **The Eight-Bit Link said:**
> I have been having a mistrusted package problem with my package managers (Synaptic, USC, ect.) Whenever I attempt to install something, USC usually starts to load after auth, then pops up saying something about a failed download due to bad net, then I get an uncheckable package error. Is there something I can do about this? I can only install things via Synaptic, and it isn't as 'friendly' as USC.

Thanks to the kind being who solves and/or explains this in advance.

Please open a terminal and post full output of ```
sudo apt-get update
``` and we will go from there.

Good Luck

---

### Post by The Eight-Bit Link on 2011-06-01
Mkay here it is.

```
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net natty InRelease                                   
Get:2 http://dl.google.com stable Release [1,351 B]                            
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.canonical.com natty Release.gpg                             
Get:3 http://dl.google.com stable/main i386 Packages [1,214 B]                 
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://ppa.launchpad.net natty Release                                     
Hit http://extras.ubuntu.com natty Release                                     
Hit http://archive.canonical.com natty Release                                 
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://security.ubuntu.com natty-security Release                          
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://archive.canonical.com natty/partner i386 Packages                   
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://dl.google.com stable/main Translation-en                  
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com natty-security/multiverse Translation-en       
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com natty-security/restricted Translation-en       
Ign http://security.ubuntu.com natty-security/universe Translation-en_US      
Ign http://security.ubuntu.com natty-security/universe Translation-en         
Ign http://us.archive.ubuntu.com natty/universe Translation-en                
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 2,763 B in 3s (805 B/s)
Reading package lists... Done

```

---

### Post by plucky on 2011-06-01
No errors there

What does ```
sudo apt-get upgrade
``` show you?

---

