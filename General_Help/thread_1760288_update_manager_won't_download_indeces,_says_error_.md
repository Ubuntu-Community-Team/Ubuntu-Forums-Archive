---
title: "update manager won't download indeces, says error check internet connect..Help!"
date: 2011-05-16
forum: General Help
---

### Post by mejbr2003 on 2011-05-16
it fails to fetch indexes. it says to check my connection. but for sure I'm connected!
I'm using natty
here's what happens when I run sudo apt-get update
help please



josh@mylivingHAL:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb InRelease                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports InRelease                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports InRelease                     
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [764 B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps i386 Packages                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main TranslationIndex      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe i386 Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main i386 Packages            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe TranslationIndex     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Translation-en_US    
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main i386 Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe i386 Packages
  404  Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.40 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Translation-en           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Translation-en       
Fetched 2,308 B in 7s (293 B/s)                                                
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
josh@mylivingHAL:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
josh@mylivingHAL:~$

---

### Post by gsmanners on 2011-05-16
You need to run Software Sources and get rid of all those "lucid" and "intrepid" sources.

---

