---
title: "Error in terminal when installing Xfce 4 Appfinder"
date: 2009-06-30
forum: General Help
---

### Post by g35celicaz on 2009-06-30
I have ubuntu 8.10 on my laptop and i wanted to installXfce 4 Appfinder. However when i put the command in the terminal window it gave me an error. 


I got the command from this website:

[http://ubuntuforums.org/showthread.php?t=182201](http://ubuntuforums.org/showthread.php?t=182201)


The command was this:

sudo apt-get update&&sudo apt-get install xfce4-appfinder

I put it in the terminal and it it gave me this:

g35celicaz@g35celicaz-laptop:~$ sudo apt-get update&&sudo apt-get install xfce4-appfinder
[sudo] password for g35celicaz: 
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030) intrepid Release.gpg
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030) intrepid/main Translation-en_US                           
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030) intrepid/restricted Translation-en_US                     
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030) intrepid Release                                          
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030) intrepid/main Packages                                    
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030) intrepid/restricted Packages                              
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030) intrepid/main Packages                                    
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030) intrepid/restricted Packages                              
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                                                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US                           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                                                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                                   
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                                      
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg [189B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                                                                   
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release [51.2kB]                                                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages [81.9kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages [14B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages [44.8kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages [1356B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources [16.3kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources [14B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources [15.5kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources [623B]
Fetched 212kB in 3s (68.3kB/s)                      
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
g35celicaz@g35celicaz-laptop:~$ 

What can I do to fix this error?

Please Help

 - Thanks

---

