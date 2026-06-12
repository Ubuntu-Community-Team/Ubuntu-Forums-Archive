---
title: "Funky error given when updating in terminal."
date: 2011-07-24
forum: General Help
---

### Post by eldonkr on 2011-07-24
A few times today I've added new repositories and installed new programs through the terminal. The most recent example I entered the following into a terminal window:

```

sudo apt-get update && sudo apt-get install glimpse glimpse-profile-elementary glimpse-profile-ubuntu

```

Then; after authenticating term spits out the following lines:

```


Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Get:3 http://dl.google.com stable Release [1,351 B]                            
Ign http://archive.canonical.com natty InRelease                               
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Get:4 http://dl.google.com stable Release [1,347 B]                            
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://security.ubuntu.com natty-security Release.gpg                      
Get:5 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Get:6 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Hit http://ppa.launchpad.net natty Release.gpg                                 
Get:7 http://dl.google.com stable/main amd64 Packages [1,257 B]                
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://archive.canonical.com natty Release                                 
Hit http://security.ubuntu.com natty-security Release                          
Hit http://extras.ubuntu.com natty Release                                     
Get:8 http://dl.google.com stable/main amd64 Packages [759 B]                  
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net natty Release.gpg                                 
Get:9 http://ppa.launchpad.net natty Release [9,738 B]                         
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://security.ubuntu.com natty-security/main Sources                     
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com natty-updates Release                         
Ign http://ppa.launchpad.net natty Release                                     
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main amd64 Packages              
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages        
Hit http://ppa.launchpad.net natty Release                                     
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main amd64 Packages                     
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://security.ubuntu.com natty-security/universe amd64 Packages          
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages        
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages               
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Get:10 http://ppa.launchpad.net natty/main Sources [1,161 B]                   
Get:11 http://ppa.launchpad.net natty/main amd64 Packages [1,133 B]            
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/main amd64 Packages             
Hit http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com natty-updates/universe amd64 Packages         
Hit http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages       
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://dl.google.com stable/main Translation-en                            
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main amd64 Packages                         
  404  Not Found
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US            
Ign http://ppa.launchpad.net natty/main Translation-en               
Ign http://ppa.launchpad.net natty/main Translation-en_US            
Ign http://ppa.launchpad.net natty/main Translation-en               
Ign http://ppa.launchpad.net natty/main Translation-en_US            
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en                         
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
Fetched 17.5 kB in 3s (5,241 B/s)
W: Failed to fetch http://ppa.launchpad.net/weather-indicator-applet-team/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/weather-indicator-applet-team/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

What does this mean? How do I go about fixing this? Is this a serious issue that I should be concerned with?

---

### Post by zombifier25 on 2011-07-24
It means that some of the repositories is not found (error 404)

No worries; everything is normal.

---

### Post by eldonkr on 2011-07-24
> **zombifier25 said:**
> It means that some of the repositories is not found (error 404)

No worries; everything is normal.

Oh, ok. Thanks!

---

### Post by bapoumba on 2011-07-24
You can remove the ppa for the weather indicator. It is now in the natty universe repos.
[http://packages.ubuntu.com/natty/indicator-weather](http://packages.ubuntu.com/natty/indicator-weather)

---

### Post by eldonkr on 2011-07-24
term command for that?

---

