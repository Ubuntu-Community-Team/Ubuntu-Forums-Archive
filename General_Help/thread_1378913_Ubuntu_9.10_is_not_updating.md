---
title: "Ubuntu 9.10 is not updating"
date: 2010-01-12
forum: General Help
---

### Post by antonyraja on 2010-01-12
when i try to update ubuntu.....it is giving me the following error.

root@raja-laptop:~# apt-get update
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg                                                                                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN                                                                                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN                                                                                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN                                                                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN                                                                                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg                                                                                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN                                                                                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN                                                                                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN                                                                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN                                                                                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release                                                                                                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release                                                                                                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages                                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources                                                                                                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources                                                                                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages                                                                                                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources                                                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages                                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources                                                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages                                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages                                                                                         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources                                                                                                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources                                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages                                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources                                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages                                                                                         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources                                                                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages                                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources                                                           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources                                                                                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages                                                                                                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources                                                                                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages                                                                                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources                                                                                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages                                                                                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages                                            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources                                                                                                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources                                                                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages                                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources                                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages                                            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources                                             
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                                                          
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages                                                    
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources                                                           
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources                                                     
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages                                                      
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources                                                       
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages                                                    
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources                                                     
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages                                                  
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages                                                                                         
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources                                                                                                
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources                                             
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages                                                                                           
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources                                                                                            
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages                                            
  400  Bad Request [IP: 111.91.91.4 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources                                             
  400  Bad Request [IP: 111.91.91.4 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IN                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                                                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                                                                        
Err [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages   
  400  Bad Request
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
  400  Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
  400  Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
  400  Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources                       
  400  Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                        
  400  Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
  400  Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
  400  Bad Request
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources                       
  400  Bad Request
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  400  Bad Request
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  400  Bad Request [IP: 111.91.91.4 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  400  Bad Request

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  400  Bad Request

W: Failed to fetch [http://ppa.launchpad.net/compiz/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/compiz/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  400  Bad Request

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mörgæs on 2010-01-12
There can be several explanations. If you boot your machine and then open the Update Manager window, you should see a list of recommended updates. 

If you first click 'Check' (I believe that is the name - I don't have 9.10) and then, when the process is finished, click 'Install Updates', how does the update run?

---

### Post by Macinbomzh on 2010-01-12
Try connecting manually (not with apt-get), it will pour more light on the situation.

---

