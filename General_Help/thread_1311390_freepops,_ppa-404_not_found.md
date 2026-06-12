---
title: "freepops, ppa-404 not found"
date: 2009-11-02
forum: General Help
---

### Post by donato roque on 2009-11-02
I am using freepops in jaunty and it works.  
  
  After I install a fresh karmic and mount /home and started using Evolution all my mail and contacts are back.  Synaptic downloaded all the software I am using before including freepops.  But its not working.  Evolution is not getting my emails.  It seemed like there is no connection with the email servers.  GUI is indicating completion but an error in password is showing up.  

  In addition when I update apt-get, the ppa for freepops is showing a 404 Not Found error message.  

  I've searched the forum but found no thread exactly the same as my concerns.  Although I've noticed threads regarding issues about people's ppa's.

---

### Post by rykel on 2009-11-08
When I do a "sudo apt-get update", I am getting a lot of 404 errors at the end too... take a look. Please help?

> aen@SuperStar:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                                                      
Get:1 [http://deb.torproject.org](http://deb.torproject.org) karmic Release.gpg [489B]                                                                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_SG                                                                           
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_SG                                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                                                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                                                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_SG                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_SG                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_SG                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                                                                    
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                                                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages                                                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                                                                              
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Translation-en_SG                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Ign [http://deb.torproject.org](http://deb.torproject.org) karmic/main Translation-en_SG                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) karmic/ Release.gpg                                                                                                   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) karmic/ Translation-en_SG                                                                                             
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) karmic/ Release                                                                                                       
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                                                                                             
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Packages                                                                                      
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) karmic/ Packages                                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                                                                                                
Get:2 [http://deb.torproject.org](http://deb.torproject.org) karmic Release [2,223B]                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                    
Ign [http://deb.torproject.org](http://deb.torproject.org) karmic Release                                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                         
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) karmic/ Packages                                                                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_SG                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                              
Ign [http://deb.torproject.org](http://deb.torproject.org) karmic/main Packages                                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_SG                                                                    
Ign [http://deb.torproject.org](http://deb.torproject.org) karmic/main Packages                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_SG                                                
Get:3 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg [197B]                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_SG                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                                                         
Hit [http://deb.torproject.org](http://deb.torproject.org) karmic/main Packages                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_SG                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_SG
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) karmic/ Packages                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_SG                                                                            
Get:4 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release [3,454B]                                                                                    
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_SG                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_SG                                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release                                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                                                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources                                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_SG                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources                                                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages    
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [3,270B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
Fetched 689B in 45s (15B/s)
W: GPG error: [http://deb.torproject.org](http://deb.torproject.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/scribus/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/scribus/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/teamgnunet/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/teamgnunet/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Thanks!!

---

### Post by donato roque on 2009-12-06
> **donato roque said:**
> I am using freepops in jaunty and it works.  
  
  After I install a fresh karmic and mount /home and started using Evolution all my mail and contacts are back.  Synaptic downloaded all the software I am using before including freepops.  But its not working.  Evolution is not getting my emails.  It seemed like there is no connection with the email servers.  GUI is indicating completion but an error in password is showing up.  

  In addition when I update apt-get, the ppa for freepops is showing a 404 Not Found error message.  

  I've searched the forum but found no thread exactly the same as my concerns.  Although I've noticed threads regarding issues about people's ppa's.

    I dropped the ppa and used the freepops available in the repository instead.  They work.  Thanks.

---

