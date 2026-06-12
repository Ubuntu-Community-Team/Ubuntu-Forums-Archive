---
title: "sudo apt-get update - what's wrong with it?"
date: 2009-06-29
forum: General Help
---

### Post by sponsoredwalk on 2009-06-29
Hi i'm on Ubuntu 7.10 Gutsy and this is my sudo apt-get update output
>  sudo apt-get update 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg                                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_IE                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_IE                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_IE                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_IE                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_IE                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_IE                                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_IE                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_IE                                                          
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [189B]                                                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_IE                                                                  
Get:2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy Release.gpg [191B]                                                                     
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/main Translation-en_IE                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg                                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_IE                                                                   
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                                                                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_IE                                                                            
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/restricted Translation-en_IE                                                                       
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/universe Translation-en_IE                                                        
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/multiverse Translation-en_IE                      
Get:4 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates Release.gpg [189B]                      
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/main Translation-en_IE                    
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/restricted Translation-en_IE              
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/universe Translation-en_IE                
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/multiverse Translation-en_IE              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_IE                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_IE                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_IE                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release                                                             
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy Release                                                                 
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates Release             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                    
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [197B]         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_IE       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_IE   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                   
  
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                                   
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/main Packages                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources              
Get:6 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release [1005B]         
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/restricted Packages        
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages             
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/main Packages      
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 1200B in 2s (468B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

It seems as though nothing is downloading or updating...

---

### Post by kerry_s on 2009-06-29
that's because 7.10 is long past dead, those repo's don't exist no more.
found it: [http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)

---

### Post by colau on 2009-06-29
> **sponsoredwalk said:**
> Hi i'm on Ubuntu 7.10 Gutsy and this is my sudo apt-get update output


It seems as though nothing is downloading or updating...
Why aren't you upgrading your system to 9.04?

---

### Post by dtoronto on 2009-06-30
I would recommend going with the 8.04.  you get the LTS support and it's been one of the most stable releases of Ubuntu available.  I've tried 8.10 and run 9.04 on one desktop, but still prefer 8.04 on my servers, office and laptop.

---

### Post by sponsoredwalk on 2009-06-30
Hi i would love to go to 9.04 but my computer has not got the ram, it's 256... i can't even run "rosegarden" without it stalling, will it be ok if i upgrade to 8.04, like i  hope it doesn't slow the computer excessively in normal tasks...AND when i tried to here is what happened:

This is what i get when i try to upgrade from 7.04 to 8.10 via the terminal, Also when i try to do it through synaptic package manager i get a similar error... I use the kernel 2.6.22-16 and i have tried to do the upgrade on 22.6.22-14 as well and it didn't work either...
> sudo do-release-upgrade
   Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool s 
Done downloading            
extracting '/tmp/tmp4Vx6mK/hardy.tar.gz'
authenticate '/tmp/tmp4Vx6mK/hardy.tar.gz' against '/tmp/tmp4Vx6mK/hardy.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg
Done [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Done [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy Release
Done [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Failed [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Done [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/main Packages
Done [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources
Done [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ignored [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Failed [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ignored [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Failed [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates Release
Ignored [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Failed [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/main Packages
Ignored [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Failed [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

Done [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Done [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ignored [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Failed [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ignored [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Failed [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
Done downloading            

Checking package manager
Reading package lists: Doneardy-proposed/universe Packages: 57     
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Support for some applications ended 

Canonical Ltd. no longer provides support for the following software 
packages. You can still get support from the community. 

If you have not enabled community maintained software (universe), 
these packages will be suggested for removal at the end of the 
upgrade. 

Demoted: 
libgdchart-gd2-noxpm, libnessus2, nessus 



Calculating the changes

Could not calculate the upgrade 

A unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bugreport. 


Restoring original system state

Aborting
Reading package lists: Donerg gutsy/non-free Packages: 91  kages: 91  
Reading state information: Done
Reading state information: Done
Reading state information: Done

---

### Post by sponsoredwalk on 2009-06-30
sorry i meant upgrade from 7.10 to 8.04^^^^ really sorry... :) Amabo te :)

---

### Post by mixmaster on 2009-06-30
Instructions for upgrading obsolete code (ie 7.10)

[http://blog.uncommons.org/2009/05/30/upgrading-obsolete-ubuntu-systems/](http://blog.uncommons.org/2009/05/30/upgrading-obsolete-ubuntu-systems/)

---

### Post by t4thfavor on 2009-06-30
Use xubuntu  instead, then you can run 9.04 just fine. if it only has 256, I would also recommend finding another PC to rob parts for an upgrad as you probably waste more time waiting for your pc than actually working.

I used one with 600mhz and 128mb and a full ubuntu gui for about 30 seconds, then switched to xubuntu and it was mostly usable.

---

### Post by sponsoredwalk on 2009-06-30
I have Xubuntu, like if i select it in options when i type my password in, that is the Xubuntu right? like that actually makes a difference is speed if i USE it?

So if i were to log in via Xubuntu on this screen, how would i go about upgrading to 9.04 via this and saving the settings so that Xubuntu is always used... 

Sorry i am having a lot of problems with my system and am not smart enough to fix them

Magna amabo te :)

---

### Post by t4thfavor on 2009-06-30
login, and start the update manager, it will tell you there is a dist upgrade available. After upgrading to whatever version you wanted to update to, execute ```
sudo apt-get remove ubuntu-desktop
``` , then next time you reboot you will either have no gui (in which case you have to install xubuntu-desktop) or you will just have xubuntu and all will be good.

The upgrade will take forever since it has to download alot of data. If you have a slow internet connection you should probably find a quiet place to download an update cd.

---

### Post by sponsoredwalk on 2009-06-30
That's so nice, thank you so much, so i'll lorg in via Xubuntu now and give it a shot. I just am worried now, you say i might have no GUI, how would i download a GUI if have nothing to use to download it? 

Amabo Te :) mihi consilium bonum das ;)

---

### Post by kerry_s on 2009-06-30
> **t4thfavor said:**
> login, and start the update manager, it will tell you there is a dist upgrade available. After upgrading to whatever version you wanted to update to, execute ```
sudo apt-get remove ubuntu-desktop
``` , then next time you reboot you will either have no gui (in which case you have to install xubuntu-desktop) or you will just have xubuntu and all will be good.

The upgrade will take forever since it has to download alot of data. If you have a slow internet connection you should probably find a quiet place to download an update cd.

ubuntu-desktop is just a meta-package, that command does not remove nothing.

---

### Post by kerry_s on 2009-06-30
> **sponsoredwalk said:**
> That's so nice, thank you so much, so i'll lorg in via Xubuntu now and give it a shot. I just am worried now, you say i might have no GUI, how would i download a GUI if have nothing to use to download it? 

Amabo Te :) mihi consilium bonum das ;)

i have debian testing xfce4 on 450mhz 256mb ram, i did a base install then built it up from there.

---

