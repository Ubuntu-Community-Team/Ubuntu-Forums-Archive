---
title: "What causes apt-get update to Ign a repo?"
date: 2011-06-11
forum: General Help
---

### Post by oldos2er on 2011-06-11
Everytime in the last couple days when I've run either apt-get update or aptitude update, [http://ppa.launchpad.net](http://ppa.launchpad.net) is ignored: ```
ann@ann-Dell-XPS410:~$ sudo aptitude update
[sudo] password for ann: 
Ign http://mirror.peer1.net natty InRelease
Ign http://mirror.peer1.net natty-updates InRelease                         
Ign http://mirror.peer1.net natty-security InRelease                        
Ign http://mirror.peer1.net natty-proposed InRelease                        
Hit http://mirror.peer1.net natty Release.gpg                               
Hit http://mirror.peer1.net natty-updates Release.gpg                       
Hit http://mirror.peer1.net natty-security Release.gpg                      
Ign http://dl.google.com stable InRelease                                   
Hit http://mirror.peer1.net natty-proposed Release.gpg                      
Hit http://mirror.peer1.net natty Release                                   
Hit http://mirror.peer1.net natty-updates Release                           
Ign http://dl.google.com stable InRelease                                   
Hit http://mirror.peer1.net natty-security Release                          
Hit http://mirror.peer1.net natty-proposed Release                          
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                
Hit http://mirror.peer1.net natty/restricted Sources                        
Hit http://mirror.peer1.net natty/main Sources                              
Hit http://mirror.peer1.net natty/multiverse Sources                        
Hit http://mirror.peer1.net natty/universe Sources                          
Hit http://mirror.peer1.net natty/main amd64 Packages                       
Hit http://mirror.peer1.net natty/restricted amd64 Packages                 
Get:1 http://dl.google.com stable Release.gpg [198 B]                       
Hit http://mirror.peer1.net natty/universe amd64 Packages                   
Hit http://mirror.peer1.net natty/multiverse amd64 Packages                 
Ign http://mirror.peer1.net natty/main TranslationIndex                     
Ign http://mirror.peer1.net natty/multiverse TranslationIndex               
Ign http://mirror.peer1.net natty/restricted TranslationIndex               
Ign http://extras.ubuntu.com natty InRelease                                
Ign http://mirror.peer1.net natty/universe TranslationIndex                 
Hit http://mirror.peer1.net natty-updates/restricted Sources                
Hit http://mirror.peer1.net natty-updates/main Sources                      
Hit http://mirror.peer1.net natty-updates/multiverse Sources                
Hit http://mirror.peer1.net natty-updates/universe Sources                  
Hit http://mirror.peer1.net natty-updates/main amd64 Packages               
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                
Ign http://archive.canonical.com natty InRelease                            
Hit http://mirror.peer1.net natty-updates/restricted amd64 Packages         
Hit http://mirror.peer1.net natty-updates/universe amd64 Packages           
Hit http://mirror.peer1.net natty-updates/multiverse amd64 Packages         
Ign http://mirror.peer1.net natty-updates/main TranslationIndex             
Ign http://mirror.peer1.net natty-updates/multiverse TranslationIndex       
Ign http://mirror.peer1.net natty-updates/restricted TranslationIndex       
Ign http://mirror.peer1.net natty-updates/universe TranslationIndex         
Hit http://mirror.peer1.net natty-security/restricted Sources               
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://mirror.peer1.net natty-security/main Sources                     
Hit http://mirror.peer1.net natty-security/multiverse Sources               
Hit http://mirror.peer1.net natty-security/universe Sources                 
Hit http://mirror.peer1.net natty-security/main amd64 Packages              
Hit http://mirror.peer1.net natty-security/restricted amd64 Packages        
Get:2 http://dl.google.com stable Release.gpg [198 B]                       
Hit http://extras.ubuntu.com natty Release.gpg                              
Hit http://mirror.peer1.net natty-security/universe amd64 Packages          
Hit http://mirror.peer1.net natty-security/multiverse amd64 Packages        
Ign http://mirror.peer1.net natty-security/main TranslationIndex            
Ign http://mirror.peer1.net natty-security/multiverse TranslationIndex      
Ign http://mirror.peer1.net natty-security/restricted TranslationIndex      
Ign http://mirror.peer1.net natty-security/universe TranslationIndex        
Hit http://mirror.peer1.net natty-proposed/restricted Sources               
Hit http://mirror.peer1.net natty-proposed/main Sources                     
Hit http://mirror.peer1.net natty-proposed/multiverse Sources               
Hit http://packages.medibuntu.org natty InRelease                           
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://archive.canonical.com natty Release.gpg                          
Hit http://mirror.peer1.net natty-proposed/universe Sources                 
Hit http://mirror.peer1.net natty-proposed/restricted amd64 Packages        
Hit http://mirror.peer1.net natty-proposed/main amd64 Packages              
Hit http://mirror.peer1.net natty-proposed/multiverse amd64 Packages        
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://mirror.peer1.net natty-proposed/universe amd64 Packages          
Ign http://mirror.peer1.net natty-proposed/main TranslationIndex            
Ign http://mirror.peer1.net natty-proposed/multiverse TranslationIndex      
Ign http://mirror.peer1.net natty-proposed/restricted TranslationIndex      
Ign http://mirror.peer1.net natty-proposed/universe TranslationIndex        
Hit http://extras.ubuntu.com natty Release                                  
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://ppa.launchpad.net natty Release.gpg                              
Get:3 http://dl.google.com stable Release [1,351 B]                         
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://archive.canonical.com natty Release                              
Hit http://ppa.launchpad.net natty Release.gpg                              
Hit http://ppa.launchpad.net natty Release                                  
Hit http://ppa.launchpad.net natty Release                                  
Hit http://ppa.launchpad.net natty Release                                  
Get:4 http://dl.google.com stable Release [1,338 B]                         
Hit http://extras.ubuntu.com natty/main Sources                             
Hit http://ppa.launchpad.net natty Release                                  
Hit http://archive.canonical.com natty/partner Sources                      
Hit http://ppa.launchpad.net natty Release                                  
Hit http://ppa.launchpad.net natty Release                                  
Hit http://ppa.launchpad.net natty Release                                  
Hit http://ppa.launchpad.net natty Release                                  
Get:5 http://dl.google.com stable/main amd64 Packages [1,213 B]             
Hit http://packages.medibuntu.org natty/free Sources                        
Hit http://extras.ubuntu.com natty/main amd64 Packages                      
Ign http://dl.google.com stable/main TranslationIndex                       
Hit http://archive.canonical.com natty/partner amd64 Packages               
Ign http://archive.canonical.com natty/partner TranslationIndex             
Hit http://ppa.launchpad.net natty Release                                  
Hit http://ppa.launchpad.net natty Release                                  
Hit http://ppa.launchpad.net natty/main Sources                             
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                             
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                             
Get:6 http://dl.google.com stable/main amd64 Packages [469 B]               
Ign http://dl.google.com stable/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                             
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Ign http://extras.ubuntu.com natty/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                             
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                             
Hit http://packages.medibuntu.org natty/non-free Sources                    
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                             
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                             
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Hit http://ppa.launchpad.net natty/main Sources                             
Ign http://mirror.peer1.net natty/main Translation-en_US                    
Ign http://mirror.peer1.net natty/main Translation-en                       
Ign http://mirror.peer1.net natty/multiverse Translation-en_US              
Ign http://mirror.peer1.net natty/multiverse Translation-en                 
Ign http://mirror.peer1.net natty/restricted Translation-en_US              
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://mirror.peer1.net natty/restricted Translation-en                 
Ign http://mirror.peer1.net natty/universe Translation-en_US                
Ign http://mirror.peer1.net natty/universe Translation-en                   
Ign http://mirror.peer1.net natty-updates/main Translation-en_US            
Ign http://mirror.peer1.net natty-updates/main Translation-en               
Ign http://mirror.peer1.net natty-updates/multiverse Translation-en_US      
Ign http://mirror.peer1.net natty-updates/multiverse Translation-en         
Ign http://mirror.peer1.net natty-updates/restricted Translation-en_US      
Ign http://mirror.peer1.net natty-updates/restricted Translation-en         
Ign http://mirror.peer1.net natty-updates/universe Translation-en_US        
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Ign http://mirror.peer1.net natty-updates/universe Translation-en           
Ign http://mirror.peer1.net natty-security/main Translation-en_US           
Ign http://mirror.peer1.net natty-security/main Translation-en              
Ign http://mirror.peer1.net natty-security/multiverse Translation-en_US     
Ign http://mirror.peer1.net natty-security/multiverse Translation-en        
Hit http://ppa.launchpad.net natty/main Sources                             
Hit http://ppa.launchpad.net natty/main amd64 Packages                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                    
Ign http://mirror.peer1.net natty-security/restricted Translation-en_US     
Ign http://mirror.peer1.net natty-security/restricted Translation-en        
Ign http://mirror.peer1.net natty-security/universe Translation-en_US       
Ign http://mirror.peer1.net natty-security/universe Translation-en          
Ign http://mirror.peer1.net natty-proposed/main Translation-en_US           
Ign http://mirror.peer1.net natty-proposed/main Translation-en              
Ign http://mirror.peer1.net natty-proposed/multiverse Translation-en_US     
Ign http://mirror.peer1.net natty-proposed/multiverse Translation-en        
Ign http://mirror.peer1.net natty-proposed/restricted Translation-en_US     
Ign http://mirror.peer1.net natty-proposed/restricted Translation-en        
Ign http://mirror.peer1.net natty-proposed/universe Translation-en_US       
Ign http://mirror.peer1.net natty-proposed/universe Translation-en          
Hit http://packages.medibuntu.org natty/free amd64 Packages                 
Ign http://archive.canonical.com natty/partner Translation-en_US            
Hit http://packages.medibuntu.org natty/non-free amd64 Packages      
Ign http://archive.canonical.com natty/partner Translation-en               
Ign http://extras.ubuntu.com natty/main Translation-en_US                   
Ign http://extras.ubuntu.com natty/main Translation-en                      
Ign http://packages.medibuntu.org natty/free TranslationIndex               
Ign http://dl.google.com stable/main Translation-en_US                      
Ign http://dl.google.com stable/main Translation-en                         
Ign http://dl.google.com stable/main Translation-en_US                      
Ign http://dl.google.com stable/main Translation-en                         
Ign http://packages.medibuntu.org natty/non-free TranslationIndex           
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
Ign http://packages.medibuntu.org natty/free Translation-en_US              
Ign http://packages.medibuntu.org natty/free Translation-en                 
Ign http://packages.medibuntu.org natty/non-free Translation-en_US          
Ign http://packages.medibuntu.org natty/non-free Translation-en             
Fetched 4,767 B in 9s (484 B/s)
```

Others are ignored too, but ppa.launchpad.net is the only one I care about. I've tried a few different mirrors with the same result. I'm able to ping ppa.launchpad.net just fine, and am not experiencing any other network weirdness.

Thanks for any pointers.

---

### Post by mc4man on 2011-06-11
Take this with  grain of salt -
 I've taken - 
 ign to mean something hasn't changed (date/name?) and to ignore, not download
hit to mean it was downloaded, no change
get - there was a change, updated

---

### Post by oldos2er on 2011-06-11
Ok, I thought 'Ign' meant APT couldn't contact the repo. Thanks for your advice.

---

### Post by CaptainMark on 2011-06-11
if apt-get cant contact the repo i thought you recieved the 404 error at the end of the output, i could be wrong

---

### Post by wildmanne39 on 2011-06-11
> **oldos2er said:**
> Ok, I thought 'Ign' meant APT couldn't contact the repo. Thanks for your advice.
Hi, it does not look like a problem, my system shows the same thing and I get all my updates fine,the other post is correct if you can not connect to a server you will get 404 error.

---

