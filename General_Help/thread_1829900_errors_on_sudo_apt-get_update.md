---
title: "errors on sudo apt-get update"
date: 2011-08-20
forum: General Help
---

### Post by oneadvent on 2011-08-20
```
oneadvent@oneadvent-desktop:/var/lib/apt$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://extras.ubuntu.com natty InRelease                        
Ign http://us.archive.ubuntu.com natty InRelease                    
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://security.ubuntu.com natty-security InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                
Get:2 http://extras.ubuntu.com natty Release.gpg [72 B]              
Get:3 http://us.archive.ubuntu.com natty Release.gpg [198 B]         
Get:4 http://security.ubuntu.com natty-security Release.gpg [198 B]                               
Get:5 http://dl.google.com stable Release [1,347 B]                                                   
Get:6 http://extras.ubuntu.com natty Release [9,753 B]                                                
Get:7 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]                          
Ign http://dl.google.com stable Release                                 
Ign http://extras.ubuntu.com natty Release                                                    
Get:8 http://security.ubuntu.com natty-security Release [31.4 kB]                             
Ign http://security.ubuntu.com natty-security Release                                                 
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex                                 
Get:9 http://us.archive.ubuntu.com natty Release [39.8 kB]           
Ign http://us.archive.ubuntu.com natty Release                                                
Ign http://extras.ubuntu.com natty/main Sources/DiffIndex                                     
Ign http://dl.google.com stable/main TranslationIndex                
Ign http://security.ubuntu.com natty-security/main Sources/DiffIndex 
Get:10 http://us.archive.ubuntu.com natty-updates Release [31.4 kB]  
Ign http://us.archive.ubuntu.com natty-updates Release                                         
Ign http://extras.ubuntu.com natty/main amd64 Packages/DiffIndex                               
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Get:11 http://dl.google.com stable/main amd64 Packages [1,184 B]                           
Ign http://us.archive.ubuntu.com natty/main Sources/DiffIndex                                              
Ign http://us.archive.ubuntu.com natty/restricted Sources/DiffIndex                        
Ign http://us.archive.ubuntu.com natty/universe Sources/DiffIndex                          
Ign http://us.archive.ubuntu.com natty/multiverse Sources/DiffIndex                        
Ign http://us.archive.ubuntu.com natty/main amd64 Packages/DiffIndex                       
Ign http://security.ubuntu.com natty-security/restricted Sources/DiffIndex                 
Ign http://security.ubuntu.com natty-security/universe Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/multiverse Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/main amd64 Packages/DiffIndex                
Ign http://security.ubuntu.com natty-security/restricted amd64 Packages/DiffIndex          
Hit http://extras.ubuntu.com natty/main Sources                      
Ign http://us.archive.ubuntu.com natty/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                               
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex                         
Ign http://security.ubuntu.com natty-security/universe amd64 Packages/DiffIndex            
Ign http://security.ubuntu.com natty-security/multiverse amd64 Packages/DiffIndex          
Ign http://security.ubuntu.com natty-security/main TranslationIndex                        
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex                         
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex                           
Ign http://us.archive.ubuntu.com natty-updates/main Sources/DiffIndex                      
Ign http://us.archive.ubuntu.com natty-updates/restricted Sources/DiffIndex                
Ign http://us.archive.ubuntu.com natty-updates/universe Sources/DiffIndex                  
Hit http://extras.ubuntu.com natty/main amd64 Packages                                     
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                    
Hit http://security.ubuntu.com natty-security/main Sources                                 
Hit http://security.ubuntu.com natty-security/restricted Sources                           
Hit http://security.ubuntu.com natty-security/universe Sources                             
Hit http://security.ubuntu.com natty-security/multiverse Sources                           
Ign http://us.archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex                
Ign http://us.archive.ubuntu.com natty-updates/main amd64 Packages/DiffIndex               
Ign http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages/DiffIndex
Hit http://security.ubuntu.com natty-security/main amd64 Packages    
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages                    
Hit http://security.ubuntu.com natty-security/universe amd64 Packages                      
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages                    
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex                 
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex                   
Hit http://us.archive.ubuntu.com natty/main Sources                  
Hit http://us.archive.ubuntu.com natty/restricted Sources            
Hit http://us.archive.ubuntu.com natty/universe Sources              
Hit http://us.archive.ubuntu.com natty/multiverse Sources            
Hit http://us.archive.ubuntu.com natty/main amd64 Packages           
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages       
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages                           
Hit http://us.archive.ubuntu.com natty-updates/main Sources                                
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources                          
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                            
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources                          
Hit http://us.archive.ubuntu.com natty-updates/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Hit http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://dl.google.com stable/main Translation-en_US               
Ign http://security.ubuntu.com natty-security/main Translation-en_US 
Ign http://security.ubuntu.com natty-security/main Translation-en    
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://dl.google.com stable/main Translation-en                  
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
Fetched 3,399 B in 4s (790 B/s)
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: Unknown error executing gpgv
W: GPG error: http://extras.ubuntu.com natty Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com natty-security Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com natty Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com natty-updates Release: Unknown error executing gpgv

```

That bottom part is the error there, I think it is because some packages may have been partially installed. I had to reboot while installing them. (system locked.)

---

