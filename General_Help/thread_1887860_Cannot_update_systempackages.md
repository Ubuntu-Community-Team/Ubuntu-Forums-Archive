---
title: "Cannot update system/packages"
date: 2011-11-28
forum: General Help
---

### Post by zaiger on 2011-11-28
Hello,

I am having trouble with updating my packages/system using the update manager and synaptic. I haven't received an update in 8 days (I have it set on immediate), and I cannot download updates through any of the usual methods. 

My system is Ubuntu 11.10 AMD64

When I try to "check" for updates with the update manager I get this error: 
> Update manager failed to download repository information

Followed by these details:
> Update manager failed to download repository information
W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

And when I try to update via Synaptic I get this error: 
> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Followed by these details:
> Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download. They have been ignored, or old ones used instead.

And finally by Terminal I get this:
> 
zaiger@linux:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted TranslationIndex
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,223 B]                
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,220 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric InRelease             
Ign [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates InRelease     
Ign [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports InRelease
Ign [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed InRelease
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric Release.gpg
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates Release.gpg
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports Release.gpg                       
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security Release.gpg                        
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed Release.gpg                        
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric Release                                     
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates Release                             
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports Release                           
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security Release                            
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed Release                            
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/restricted Sources                          
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/main Sources                                
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/universe Sources                            
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/multiverse Sources                          
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/main amd64 Packages                         
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/restricted amd64 Packages                   
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/multiverse amd64 Packages                   
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/universe amd64 Packages                     
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/main i386 Packages                          
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/restricted i386 Packages                    
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/multiverse i386 Packages                    
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/universe i386 Packages                      
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/main TranslationIndex                       
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/multiverse TranslationIndex                 
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/restricted TranslationIndex                 
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/universe TranslationIndex                   
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/restricted Sources                  
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/main Sources                        
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/universe Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/multiverse Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/main amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/restricted amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/multiverse amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/universe amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/main i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/restricted i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/multiverse i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/universe i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/main TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/multiverse TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/restricted TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/universe TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/main Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/restricted Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/universe Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/multiverse Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/main amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/restricted amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/universe amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/multiverse amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/main i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/restricted i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/universe i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/multiverse i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/main TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/multiverse TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/restricted TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/universe TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/restricted Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/main Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/universe Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/multiverse Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/main amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/restricted amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/multiverse amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/universe amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/main i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/restricted i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/multiverse i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/universe i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/main TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/multiverse TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/restricted TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/universe TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/restricted Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/main Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/universe Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/multiverse Sources
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/restricted amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/main amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/universe amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/multiverse amd64 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/restricted i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/main i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/universe i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/multiverse i386 Packages
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/main TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/multiverse TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/restricted TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/universe TranslationIndex
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/main Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/multiverse Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/restricted Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric/universe Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/main Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/multiverse Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/restricted Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-updates/universe Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/main Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/multiverse Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/restricted Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-backports/universe Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/main Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/multiverse Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/restricted Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-security/universe Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/main Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/multiverse Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/restricted Translation-en
Hit [http://mirrors.mit.edu](http://mirrors.mit.edu) oneiric-proposed/universe Translation-en
Fetched 3,988 B in 46s (86 B/s)
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.


I don't know why it thinks I am trying to download a CD rom. How can I get around this so that I can update my packages? Thanks in advanced.

---

### Post by zaiger on 2011-11-28
I'm sorry, I ended up fixing it by removing all of the checks for the 11.10 CD in the update manager settings. I always end up figuring it out right after I post a thread (after days of trying). lol thanks.

---

