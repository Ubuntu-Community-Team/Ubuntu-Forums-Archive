---
title: "Natty 32bit is giving me the error “a problem occurred when checking for updates”"
date: 2011-12-22
forum: General Help
---

### Post by AlexOnVinyl on 2011-12-22
I've already tried doing what was listed here: Update manager: "A problem occurred when checking for the updates" but it didnt work.

Every time I click on the red circle with the line through it the update manager pops up and then goes away.

When I try to do ```
sudo apt-get update && sudo apt-get upgrade
```

here's the output:
```
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.getdeb.net natty-getdeb InRelease                           
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Get:3 http://dl.google.com stable Release [1,347 B]                            
Ign http://archive.canonical.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://deb.torproject.org natty InRelease                                  
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://dl.google.com stable/main i386 Packages [1,214 B]                 
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.ubuntu.com natty Release.gpg                                
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://archive.getdeb.net natty-getdeb Release.gpg                         
Ign http://deb.paissad.net unstable InRelease                                  
Get:6 http://dl.google.com stable/main i386 Packages [765 B]                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com natty Release                                 
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://extras.ubuntu.com natty Release                                     
Hit http://security.ubuntu.com natty-security Release                          
Hit http://archive.ubuntu.com natty Release                                    
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://deb.paissad.net unstable Release.gpg                                
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Hit http://deb.torproject.org natty/main Sources                               
Hit http://archive.getdeb.net natty-getdeb Release                             
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://archive.canonical.com natty/partner i386 Packages                   
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://deb.paissad.net unstable Release                                    
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://archive.getdeb.net natty-getdeb/games i386 Packages                 
Hit http://deb.paissad.net unstable/main Sources                               
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://deb.torproject.org natty/main i386 Packages                         
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://deb.paissad.net unstable/contrib Sources                            
Hit http://deb.paissad.net unstable/non-free Sources                           
Hit http://deb.paissad.net unstable/main i386 Packages                         
Hit http://deb.paissad.net unstable/contrib i386 Packages                      
Hit http://deb.paissad.net unstable/non-free i386 Packages                     
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Ign http://archive.getdeb.net natty-getdeb/games TranslationIndex              
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://deb.paissad.net unstable/contrib TranslationIndex                   
Ign http://deb.paissad.net unstable/main TranslationIndex                      
Ign http://deb.paissad.net unstable/non-free TranslationIndex                  
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://deb.torproject.org natty/main TranslationIndex                      
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://deb.paissad.net unstable/contrib Translation-en_US                  
Ign http://deb.paissad.net unstable/contrib Translation-en                     
Ign http://deb.paissad.net unstable/main Translation-en_US                     
Ign http://deb.paissad.net unstable/main Translation-en                        
Ign http://deb.paissad.net unstable/non-free Translation-en_US                 
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://deb.paissad.net unstable/non-free Translation-en                    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://archive.getdeb.net natty-getdeb/games Translation-en_US             
Ign http://archive.getdeb.net natty-getdeb/games Translation-en                
Ign http://deb.torproject.org natty/main Translation-en_US                 
Ign http://deb.torproject.org natty/main Translation-en
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Fetched 5,069 B in 9s (544 B/s)                                                
Reading package lists... Done
Reading package lists... Done
alex@griever:~$ ncy tree... 50%
```

and stops there.... doesnt move past the 50% or something

anyone have any advice?

---

