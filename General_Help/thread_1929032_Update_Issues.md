---
title: "Update Issues"
date: 2012-02-21
forum: General Help
---

### Post by Hiuhu on 2012-02-21
Hi guyz, today I tried to update my update manager and it says that it Requires installation of untrusted packages then I ran sudo apt-get update and this is what I get```

jemoh@Hiuhu:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en                 
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en      
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable/non-free Translation-en
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en_US   
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable/non-free Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports Release.gpg                
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-backports/partner Translation-en
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources/DiffIndex           
Ign [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) maverick/main Translation-en
Ign [http://download.skype.com](http://download.skype.com) stable/non-free i386 Packages/DiffIndex          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-backports/partner Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages/DiffIndex     
Ign [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://download.skype.com](http://download.skype.com) stable/non-free i386 Packages                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates Release.gpg                  
Ign [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages/DiffIndex               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://download.skype.com](http://download.skype.com) stable/non-free i386 Packages                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages/DiffIndex                   
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages               
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages                         
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources/DiffIndex                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed Release.gpg                   
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US         
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages/DiffIndex             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                             
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages                         
Err [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources                     
  400  Bad Request
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources/DiffIndex              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Err [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages               
  400  Bad Request
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources/DiffIndex          
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Err [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages                         
  400  Bad Request [IP: 209.85.229.190 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Err [http://download.skype.com](http://download.skype.com) stable/non-free i386 Packages                    
  400  Bad Request
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages/DiffIndex        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
  400  Bad Request [IP: 209.85.229.190 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages/DiffIndex    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
  400  Bad Request
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
  400  Bad Request
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-updates/partner Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) maverick/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) maverick/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed Release                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources/DiffIndex    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources/DiffIndex  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages/DiffIndex  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages/DiffIndex
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages/DiffIndex
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main Sources/DiffIndex        
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted Sources/DiffIndex  
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick Release                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe Sources/DiffIndex    
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse Sources/DiffIndex  
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main Sources/DiffIndex               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main i386 Packages/DiffIndex  
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted Sources/DiffIndex         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted i386 Packages/DiffIndex
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe i386 Packages/DiffIndex
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe Sources/DiffIndex           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse i386 Packages/DiffIndex
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main i386 Packages/DiffIndex         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-updates/partner Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security Release.gpg                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                        
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-security/partner Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  400  Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-security/partner Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
  400  Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main Sources/DiffIndex       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed Release.gpg                 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  400  Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main Sources                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main i386 Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe i386 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted Sources/DiffIndex 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages              
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse Sources/DiffIndex 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-proposed/partner Translation-en
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                        
  400  Bad Request
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe Sources/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                    
  400  Bad Request
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-proposed/partner Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main i386 Packages/DiffIndex 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                  
  400  Bad Request
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports Release                    
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages              
  400  Bad Request
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates Release                      
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main Sources                  
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security Release                     
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main Sources                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
  400  Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted Sources            
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed Release                     
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted Sources                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  400  Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe Sources              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources/DiffIndex            
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse Sources                   
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe Sources                     
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main i386 Packages                   
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted i386 Packages   
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse i386 Packages   
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe i386 Packages     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
  400  Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main i386 Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe i386 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse i386 Packages      
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main Sources                  
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted Sources            
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe Sources              
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse Sources            
  400  Bad Request [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main i386 Packages            
  400  Bad Request [IP: 91.189.92.166 80]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main Sources                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted i386 Packages      
  400  Bad Request [IP: 91.189.92.166 80]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted Sources           
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe i386 Packages        
  400  Bad Request [IP: 91.189.92.166 80]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse Sources           
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse i386 Packages      
  400  Bad Request [IP: 91.189.92.166 80]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe Sources             
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main i386 Packages           
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main Sources                         
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted Sources                   
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse Sources                   
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe Sources
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main i386 Packages                   
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted i386 Packages             
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse i386 Packages             
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe i386 Packages               
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main Sources                 
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted Sources           
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse Sources           
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe Sources             
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main i386 Packages           
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main Sources                         
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted Sources                   
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse Sources                   
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe Sources                     
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main i386 Packages                   
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted i386 Packages             
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse i386 Packages             
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe i386 Packages               
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main Sources                 
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted Sources           
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse Sources           
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe Sources             
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main i386 Packages           
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
  400  Bad Request
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe i386 Packages       
  400  Bad Request
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages/DiffIndex      
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner Sources/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner Sources/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner Sources/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner Sources/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner i386 Packages
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner Sources
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner i386 Packages
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner Sources
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner i386 Packages
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner Sources
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner i386 Packages
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner Sources
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner i386 Packages
  400  Bad Request [IP: 91.189.88.33 80]
W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/source/Sources.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/non-free/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/non-free/binary-i386/Packages.gz)  400  Bad Request [IP: 209.85.229.190 80]

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz)  400  Bad Request [IP: 209.85.229.190 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/source/Sources.gz](http://packages.medibuntu.org/dists/maverick/free/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/maverick/non-free/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/maverick/non-free/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/main/source/Sources.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/universe/source/Sources.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.166 80]

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-backports/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick-backports/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-backports/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick-backports/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-updates/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick-updates/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-updates/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick-updates/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-security/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick-security/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-security/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick-security/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-proposed/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick-proposed/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-proposed/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick-proposed/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```
Now when I try to install an application from ubuntu software centre it still tells me, requires installation of untrusted packages. Kindly pls someone help.

---

### Post by raja.genupula on 2012-02-21
* open update manager -> settings -> at download from , change your mirror to other and try again . 

if your  issue not solved then do this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

lemme know what you got , all the best .

---

### Post by Hiuhu on 2012-02-23
Hi Raja ? if I try to change the mirror all it tells me is 'No suitable server found'

---

### Post by winh8r on 2012-02-23
Go to System> Preferences> Network Proxy

make sure  "direct internet connection" is selected

then click on the "ignored hosts" tab and make sure that the only entries in the box are as follows:

localhost
127.0.0.0/8
*.local

let us know how this goes.

---

### Post by Hiuhu on 2012-02-23
Thanx for the procedure but when I use it I still get the same results. Is there any other solution ?

---

### Post by winh8r on 2012-02-23
Open a terminal and enter :

```
ping -c 5 91.189.92.166
```

post the result please.





EDIT*** can you confirm that you are not using Tor/privoxy.

---

