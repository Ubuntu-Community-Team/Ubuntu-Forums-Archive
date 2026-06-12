---
title: "Unable to access Synaptic/Software Center/Update Manager"
date: 2011-05-10
forum: General Help
---

### Post by ChaosChris2009 on 2011-05-10
I can no longer update via Update Manager after updating Natty today.

Software Center was trying to update the cache, and I accidentally got disconnected from my network connection temporarily.

Software does not show anything at all, none of my sources, installed software, not even search results while searching for software.

Update manager gives me this

[IMG]http://i.imgur.com/8OZLb.jpg[/IMG]

And Synaptic gives me this

[IMG]http://i.imgur.com/PH631.jpg[/IMG]

Please help me

---

### Post by Smart Viking on 2011-05-10
Run in terminal:
```
sudo apt-get update
```

---

### Post by ChaosChris2009 on 2011-05-10
> **Smart Viking said:**
> Run in terminal:
```
sudo apt-get update
```

Still the same

Here's the output of ```
sudo apt-get update
```

```
Ign http://mirror.hmc.edu natty InRelease
Ign http://mirror.hmc.edu natty-updates InRelease                              
Ign http://mirror.hmc.edu natty-security InRelease                             
Hit http://mirror.hmc.edu natty Release.gpg                                    
Hit http://mirror.hmc.edu natty-updates Release.gpg                            
Hit http://mirror.hmc.edu natty-security Release.gpg                           
Ign http://dl.google.com stable InRelease                                      
Hit http://mirror.hmc.edu natty Release                                        
Ign http://dl.google.com stable InRelease                                      
Hit http://mirror.hmc.edu natty-updates Release                                
Ign http://linux.dropbox.com maverick InRelease                                
Hit http://mirror.hmc.edu natty-security Release                               
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://mirror.hmc.edu natty/main Sources                                   
Hit http://linux.dropbox.com maverick Release.gpg                              
Hit http://mirror.hmc.edu natty/restricted Sources                             
Hit http://mirror.hmc.edu natty/universe Sources                               
Hit http://mirror.hmc.edu natty/multiverse Sources                             
Hit http://mirror.hmc.edu natty/main i386 Packages                             
Hit http://mirror.hmc.edu natty/restricted i386 Packages                       
Hit http://mirror.hmc.edu natty/universe i386 Packages                         
Hit http://mirror.hmc.edu natty/multiverse i386 Packages                       
Ign http://mirror.hmc.edu natty/main TranslationIndex                          
Ign http://mirror.hmc.edu natty/multiverse TranslationIndex                    
Ign http://mirror.hmc.edu natty/restricted TranslationIndex                    
Ign http://mirror.hmc.edu natty/universe TranslationIndex                      
Hit http://linux.dropbox.com maverick Release                                  
Get:2 http://dl.google.com stable Release.gpg [197 B]                          
Hit http://mirror.hmc.edu natty-updates/main Sources                           
Hit http://mirror.hmc.edu natty-updates/restricted Sources                     
Hit http://mirror.hmc.edu natty-updates/universe Sources                       
Hit http://mirror.hmc.edu natty-updates/multiverse Sources                     
Hit http://mirror.hmc.edu natty-updates/main i386 Packages                     
Hit http://mirror.hmc.edu natty-updates/restricted i386 Packages               
Hit http://mirror.hmc.edu natty-updates/universe i386 Packages                 
Hit http://mirror.hmc.edu natty-updates/multiverse i386 Packages               
Ign http://mirror.hmc.edu natty-updates/main TranslationIndex                  
Ign http://mirror.hmc.edu natty-updates/multiverse TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/restricted TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/universe TranslationIndex              
Hit http://mirror.hmc.edu natty-security/main Sources                          
Hit http://mirror.hmc.edu natty-security/restricted Sources                    
Hit http://mirror.hmc.edu natty-security/universe Sources                      
Hit http://mirror.hmc.edu natty-security/multiverse Sources                    
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://mirror.hmc.edu natty-security/main i386 Packages                    
Hit http://mirror.hmc.edu natty-security/restricted i386 Packages              
Hit http://mirror.hmc.edu natty-security/universe i386 Packages                
Hit http://mirror.hmc.edu natty-security/multiverse i386 Packages              
Ign http://mirror.hmc.edu natty-security/main TranslationIndex                 
Ign http://mirror.hmc.edu natty-security/multiverse TranslationIndex           
Ign http://mirror.hmc.edu natty-security/restricted TranslationIndex           
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Get:3 http://dl.google.com stable Release [1,347 B]                            
Ign http://mirror.hmc.edu natty-security/universe TranslationIndex             
Ign http://linux.dropbox.com maverick/main TranslationIndex                    
Get:4 http://dl.google.com stable Release [1,347 B]                            
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Get:5 http://archive.canonical.com natty Release.gpg [198 B]                   
Hit http://extras.ubuntu.com natty Release.gpg                                 
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://deb.opera.com stable InRelease                                      
Get:6 http://dl.google.com stable/main i386 Packages [1,063 B]                 
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Get:7 http://archive.canonical.com natty Release [5,916 B]                     
Hit http://extras.ubuntu.com natty Release                                     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Get:8 http://dl.google.com stable/main i386 Packages [764 B]                   
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://deb.opera.com stable Release                                        
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ppa.launchpad.net natty Release                                     
Get:9 http://archive.canonical.com natty/partner i386 Packages [7,475 B]       
Ign http://linux.dropbox.com maverick/main Translation-en_US                   
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://mirror.hmc.edu natty/main Translation-en_US                         
Ign http://mirror.hmc.edu natty/main Translation-en                            
Ign http://mirror.hmc.edu natty/multiverse Translation-en_US                   
Ign http://linux.dropbox.com maverick/main Translation-en                      
Ign http://mirror.hmc.edu natty/multiverse Translation-en                      
Ign http://mirror.hmc.edu natty/restricted Translation-en_US                   
Ign http://mirror.hmc.edu natty/restricted Translation-en                      
Ign http://mirror.hmc.edu natty/universe Translation-en_US                     
Ign http://mirror.hmc.edu natty/universe Translation-en                        
Ign http://mirror.hmc.edu natty-updates/main Translation-en_US                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://mirror.hmc.edu natty-updates/main Translation-en                    
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en_US           
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en              
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en_US           
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en              
Ign http://mirror.hmc.edu natty-updates/universe Translation-en_US             
Ign http://mirror.hmc.edu natty-updates/universe Translation-en                
Ign http://mirror.hmc.edu natty-security/main Translation-en_US                
Ign http://mirror.hmc.edu natty-security/main Translation-en                   
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en_US          
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en             
Ign http://mirror.hmc.edu natty-security/restricted Translation-en_US          
Ign http://mirror.hmc.edu natty-security/restricted Translation-en             
Ign http://mirror.hmc.edu natty-security/universe Translation-en_US            
Ign http://mirror.hmc.edu natty-security/universe Translation-en               
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://deb.opera.com stable/non-free Translation-en_US           
Ign http://deb.opera.com stable/non-free Translation-en              
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
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Fetched 18.5 kB in 10s (1,839 B/s)                                             
W: Failed to fetch http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/iaz/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/iaz/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stretch/bitcoin/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stretch/bitcoin/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by ChaosChris2009 on 2011-05-10
Bump, still haven't resolved this issue.

---

### Post by ChaosChris2009 on 2011-05-11
Please help. 

:(

---

### Post by ~Plue on 2011-05-11
> **ChaosChris2009 said:**
> ```
        
W: Failed to fetch [http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/iaz/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/iaz/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/iaz/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stretch/bitcoin/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/stretch/bitcoin/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stretch/bitcoin/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/stretch/bitcoin/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
Remove those PPAs from your sources in synaptic>settings>repositories - or any other way you want. 
(The first one doesn't exist, the second offers only Jaunty builds, and the last one doesn't have packages for Natty.)

---

