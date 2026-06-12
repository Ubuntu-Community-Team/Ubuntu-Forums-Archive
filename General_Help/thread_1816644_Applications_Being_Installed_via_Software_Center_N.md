---
title: "Applications Being Installed via Software Center Not Working!"
date: 2011-08-02
forum: General Help
---

### Post by Reyjaka on 2011-08-02
Hello, I just installed Ubuntu three(3) days ago and am having some problems installing any sort of software via the Software Center, the main problem I get is either the program installation hanging at "Waiting for apt-get to exit" When Software Center is the only program open, or an "Unhandlable Error" occuring followed by another error window stating that "Aptd Has Stopped Working"

This error has been going on since I hit Alt+F4 on a "Microsoft True Font Type" installation a few hours ago, but since then I have been able to enter the command > sudo apt-get update and produce no errors in the terminal, however I may have missed something that I do not recognize seeing I am new to this O.S. so I will include the terminal response to > sudo apt-get update

```
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Get:2 http://dl.google.com stable Release [1,351 B]                            
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://security.ubuntu.com natty-security InRelease                        
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.canonical.com natty Release.gpg                             
Get:3 http://dl.google.com stable/main i386 Packages [1,273 B]                 
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://extras.ubuntu.com natty Release                                     
Hit http://archive.canonical.com natty Release                                 
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://security.ubuntu.com natty-security Release                
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
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
Fetched 2,822 B in 8s (332 B/s)                                                
Reading package lists... Done
```

I also tried the > sudo apt-get upgrade command and got the following 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

```

How will I be able to fix this? Is there a way? Please Help!

---

### Post by turtle153 on 2011-08-02
Do you have the Software Centre open while you run that command?

---

### Post by Reyjaka on 2011-08-02
It was not open for either of them.

---

### Post by Jouke S on 2011-08-02
This error usually occurs if you have multiple package installing instances open (software center, terminal). Close all besides the one you plan on using and try again. 

If you're sure the windows are closed and the errors keep occurring, paste 'sudo rm -rf /var/cache/apt/archives/lock' into a Terminal and try again.

---

### Post by Reyjaka on 2011-08-02
That seems to have fixed the problem for now, I should mark this as solved for now? or should I leave it as-is until I am sure the problem is solved?

---

