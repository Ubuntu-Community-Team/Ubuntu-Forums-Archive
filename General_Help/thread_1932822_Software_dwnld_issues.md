---
title: "Software dwnld issues"
date: 2012-02-28
forum: General Help
---

### Post by Hiuhu on 2012-02-28
I have a little issue here. Today, when I changed my repository server from finland to russia my ubuntu software center now does not display the option of downloading softwares. What could be the problem ?

---

### Post by raja.genupula on 2012-02-28
please give me update of ```
sudo apt-get update
``` and do you have other alternative pkg manager with you(Synaptic) , if yes how it sounds when you wanna install some thing .

---

### Post by Hiuhu on 2012-02-28
Ok. Here it is;
```
jemoh@Hiuhu:~$ sudo apt-get update
Ign [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                                                                                  
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny/non-free Translation-en                                                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                                                                                                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                                                                               
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny/non-free Translation-en_US                                                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                                      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed Release.gpg                                                                                                           
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                                                                                                                       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US                                                                                            
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                            
Ign [http://deb.opera.com](http://deb.opera.com) lenny Release                                                                                                                                 
Ign [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/) maverick/main Translation-en                                                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en                                                                                           
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US                                                                                                   
Ign [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable/non-free Translation-en                                                                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports Release.gpg                                                                                                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                                                                                                                 
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en                                                                                                         
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free i386 Packages                                                                                                                  
Ign [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/) maverick/main Translation-en_US                                                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US                                                                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                                                                                          
Ign [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable/non-free Translation-en_US                                                                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-backports/partner Translation-en                                                                                     
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                                                                                                        
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US                                                                                                      
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free i386 Packages                                                                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en                                                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                                                                     
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick Release.gpg                                                                                                                      
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Ign [http://download.skype.com](http://download.skype.com) stable Release                                                                                                                           
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-backports/partner Translation-en_US                                                                                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US                                                                                                     
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en                                                                                                     
Err [http://deb.opera.com](http://deb.opera.com) lenny/non-free i386 Packages                                                                                                                  
  400  Bad Request
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en                                                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US                                                                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                                                               
Ign [http://download.skype.com](http://download.skype.com) stable/non-free i386 Packages                                                                                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates Release.gpg                                                                                                          
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en                                                                                                    
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US                                                                                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en                                                                                     
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US                                                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                                                                     
Ign [http://download.skype.com](http://download.skype.com) stable/non-free i386 Packages                                                                                                            
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-updates/partner Translation-en                                                                                       
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US                                                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US                                                                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                                                               
Err [http://download.skype.com](http://download.skype.com) stable/non-free i386 Packages                                                                                                            
  400  Bad Request
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-updates/partner Translation-en_US                                                                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                                                                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages                                                                                                                 
Ign [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) maverick/main Translation-en                                                                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en                                                                                       
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                                                                     
  400  Bad Request
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security Release.gpg                                                                                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                                                                                                                
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                                     
Ign [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) maverick/main Translation-en_US                                                                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US                                                                                    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                                                               
  400  Bad Request
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-security/partner Translation-en                                                                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                                                                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed Release                                                                                                               
Ign [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-security/partner Translation-en_US                                                                                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                                                                                                          
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) maverick/main Translation-en                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main Sources                                                                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed Release.gpg                                                                                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages                                                                                                      
Err [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages                                                                                                                 
  400  Bad Request [IP: 173.194.34.100 80]
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) maverick/main Translation-en_US                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted Sources                                                                                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-proposed/partner Translation-en                                                                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                                                                                                                
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                                     
  400  Bad Request [IP: 173.194.34.100 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe Sources                                                                                                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick-proposed/partner Translation-en_US                                                                                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                                                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse Sources                                                                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                                                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                                                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main i386 Packages                                                                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports Release                                                                                                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages                                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted i386 Packages                                                                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates Release                                                                                                              
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                                                                                                                
  400  Bad Request
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security Release                                                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe i386 Packages                                                                                                
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                                                                                                            
  400  Bad Request
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse i386 Packages                                                                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed Release                                                                                                             
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                                                                                                          
  400  Bad Request
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                                                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main Sources                                                                                                          
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages                                                                                                      
  400  Bad Request
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted Sources                                                                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe Sources                                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner Sources                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse Sources                                                                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner i386 Packages                                                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main i386 Packages                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner Sources                                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted i386 Packages                                                                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner i386 Packages                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe i386 Packages                                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner Sources                                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse i386 Packages                                                                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner i386 Packages                                                                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main Sources                                                                                                          
  400  Bad Request [IP: 91.189.92.167 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner Sources                                                                                                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted Sources                                                                                                    
  400  Bad Request [IP: 91.189.92.167 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner i386 Packages                                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe Sources                                                                                                      
  400  Bad Request [IP: 91.189.92.167 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                                                                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse Sources                                                                                                    
  400  Bad Request [IP: 91.189.92.167 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                                                                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/main i386 Packages                                                                                                    
  400  Bad Request [IP: 91.189.92.167 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner Sources                                                                                                    
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/restricted i386 Packages                                                                                              
  400  Bad Request [IP: 91.189.92.167 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-backports/partner i386 Packages                                                                                              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
  400  Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/universe i386 Packages                                                                                                
  400  Bad Request [IP: 91.189.92.167 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner Sources                                                                                                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-proposed/multiverse i386 Packages                                                                                              
  400  Bad Request [IP: 91.189.92.167 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
  400  Bad Request
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-updates/partner i386 Packages                                                                                                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                 
  400  Bad Request
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner Sources                                                                                 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                        
  400  Bad Request
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-security/partner i386 Packages                                                                        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                 
  400  Bad Request
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner Sources                                                                                 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                     
  400  Bad Request
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick-proposed/partner i386 Packages                                                                                               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                                                                     
  400  Bad Request
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                                                                                              
  400  Bad Request [IP: 91.189.88.33 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                                                                               
  400  Bad Request
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
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release.gpg               
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en_US             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release                                    
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources                               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages
Err [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources
  400  Bad Request
Err [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages
  400  Bad Request
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick/main Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick/main Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick/multiverse Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick/multiverse Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick/universe Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick/universe Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates Release.gpg
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-updates/main Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-updates/main Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-updates/multiverse Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-updates/multiverse Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-updates/universe Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-updates/universe Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security Release.gpg
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-security/main Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-security/main Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-security/multiverse Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-security/multiverse Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-security/universe Translation-en
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com/ubuntu/](http://mirrors.dnepr.com/ubuntu/) maverick-security/universe Translation-en_US
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick Release
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates Release
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security Release
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/main i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/multiverse i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/universe i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/main i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/multiverse i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/universe i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/main i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/universe i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/multiverse i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/main i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/multiverse i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/universe i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/main i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/multiverse i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/universe i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/main i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/universe i386 Packages
Ign [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/multiverse i386 Packages
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/main i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/multiverse i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick/universe i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/main i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/multiverse i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-updates/universe i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/main i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/universe i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
Err [http://mirrors.dnepr.com](http://mirrors.dnepr.com) maverick-security/multiverse i386 Packages
  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/Release.gpg](http://mirrors.dnepr.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/Release.gpg](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/Release.gpg)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/Release.gpg](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://deb.opera.com/opera/dists/lenny/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/lenny/non-free/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/non-free/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/non-free/binary-i386/Packages.gz)  400  Bad Request [IP: 173.194.34.100 80]

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz)  400  Bad Request [IP: 173.194.34.100 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/source/Sources.gz](http://packages.medibuntu.org/dists/maverick/free/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/maverick/non-free/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/maverick/free/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/maverick/non-free/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/main/source/Sources.gz)  400  Bad Request [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz)  400  Bad Request [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/universe/source/Sources.gz)  400  Bad Request [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz)  400  Bad Request [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.167 80]

W: Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.167 80]

W: Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.92.167 80]

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-backports/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick-backports/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-backports/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick-backports/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-updates/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick-updates/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-updates/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick-updates/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-security/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick-security/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-security/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick-security/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-proposed/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick-proposed/partner/source/Sources.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick-proposed/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick-proposed/partner/binary-i386/Packages.gz)  400  Bad Request [IP: 91.189.88.33 80]

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/source/Sources.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://mirrors.dnepr.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://mirrors.dnepr.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'mirrors.dnepr.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
And this is what the synaptic sounds: 
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

---

### Post by raja.genupula on 2012-02-28
Ok here we go 

look at this 

[http://www.tuxgarage.com/2011/02/something-wicked-happened-resolving-no.html](http://www.tuxgarage.com/2011/02/something-wicked-happened-resolving-no.html)

let us know what you got .all the best .

---

### Post by Hiuhu on 2012-02-28
I did exactly what the link says and the problem is still the same. What should I do ?

---

### Post by raja.genupula on 2012-02-28
after setting dns also still you have the issue ? please provide me the output, may be i can find some change .

---

### Post by Hiuhu on 2012-02-28
I still have the issue and this what the terminal says:
[http://pastebin.com/g8n12Nfx](http://pastebin.com/g8n12Nfx)

---

### Post by raja.genupula on 2012-02-28
Have you did any modifications to nameserver in  /etc/resolv.conf ? check it out once . 

if nameserver not mentioned properly then we are supposed to get errors like that , i think probably thats the problem . make a look at that once. 

Howz your update manager sounds before your switching mirror ?

---

