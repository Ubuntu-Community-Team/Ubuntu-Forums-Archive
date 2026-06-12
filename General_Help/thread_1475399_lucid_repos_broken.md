---
title: "lucid repos broken?"
date: 2010-05-06
forum: General Help
---

### Post by iceman30ad on 2010-05-06
i am having trouble downloading lists from the repositories...any one know whats going on 

im getting these error messages

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)


Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

---

### Post by iceman30ad on 2010-05-06
more info if helps
chris@chris-laptop:~$ sudo apt-get update
[sudo] password for chris: 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages               
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                   
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                            
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US                                                                                                  
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                                                                                                                     
Get:6 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1,010B]                                                                                                           
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                                                         
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/) lucid/main Translation-en_US                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                                                         
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) lucid/main Translation-en_US                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                                                         
Ign [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/) lucid/main Translation-en_US                                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                                                         
Ign [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) lucid/main Translation-en_US                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                                                         
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                                                                       
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                                                                                                     
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://download.skype.com](http://download.skype.com) stable Release.gpg                            
  Something wicked happened resolving 'download.skype.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable/non-free Translation-en_US
Ign [http://download.skype.com](http://download.skype.com) stable Release
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Fetched 10.8kB in 25s (426B/s)
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg](http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg)  Something wicked happened resolving 'download.skype.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
chris@chris-laptop:~$

---

### Post by pemadorje on 2010-05-06
I've been having this same issue on two different machines since I did a fresh install of Lucid over the weekend. I haven't been able to resolve the issue. 

I posted about the issue in the following thread but don't know if that is the best place for it because it seems to be related to someone using a proxy and I am not. 
[http://ubuntuforums.org/showthread.php?t=1466944](http://ubuntuforums.org/showthread.php?t=1466944)

For me, as long as I leave the default repositories and do a apt-get update... it runs fine. As soon as I add a few third party repositories, I start getting these errors. Also, it's bizarre because if I run apt-get a few times in a row, it's not the same repo that fails each time.

---

### Post by iceman30ad on 2010-05-07
not using a proxy either starting to look like a time out issue with the servers wish i knew how to adjust that

---

### Post by byStanderone on 2010-05-07
...if i recall correctly, have read something about this in the forum, it has to do with unchecking the cd as software source, will try to search for it, seems the cd is checked on by default.

---

### Post by iceman30ad on 2010-05-07
cd is not checked  and  i tried  removing  repos and  the ones  that were getting skiped  work just fine now  but  add even  one  and  it  starts skipping does any one know  about a bug for this  or is it that hit and miss

---

### Post by Aurora@FleetBuzz on 2010-05-07
I'm having similar issues with certain repositories in synaptic.  I noted this bug report.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

---

### Post by michael_schmid on 2010-05-07
@OP:

Have you tried enabling a mirror site instead of the main repository? Could be worth a try. One word of warning though:

don't use the *.at mirrors they seem to be badly broken. I'm from Austria and these mirrors are completely unusable since the release of 10.04.

---

### Post by iceman30ad on 2010-05-07
trying it now (not much of a geek yet but working on it)

hell-a lot faster

but still getting errors

Failed to fetch [http://ubuntu.osuosl.org/ubuntu/dists/lucid/Release.gpg](http://ubuntu.osuosl.org/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ubuntu.osuosl.org:http' (-5 - No address associated with hostname)

Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

Some index files failed to download, they have been ignored, or old ones used instead.

the urls lead to the authenticating keys is that right?

---

### Post by michael_schmid on 2010-05-07
Good to hear that you could improve your download speed. The Release.gpg files are there to verify the authenticity of the downloads. The error message is really strange though.

What happens if your try your "apt-get" line with the "--allow-unauthenticated" option (although you loose download integrity verification, so this option isn't recommended)?

---

### Post by michael_schmid on 2010-05-07
One more question: do you use a proxy to access the web (e.g. applying updates from your workplace)?

---

### Post by iceman30ad on 2010-05-07
no not using a proxy

try it and this is what i got 

chris@chris-laptop:~$ sudo apt-get update --allow-unauthenticated
[sudo] password for chris: 
Get:1 [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid Release.gpg [189B]
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid/main Translation-en_US              
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid/restricted Translation-en_US        
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid/universe Translation-en_US          
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid/multiverse Translation-en_US        
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates Release.gpg                         
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid-updates/main Translation-en_US      
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid-updates/universe Translation-en_US  
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security Release.gpg                        
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid-security/main Translation-en_US     
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid-security/universe Translation-en_US 
Ign [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid Release                                     
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates Release                             
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security Release                            
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid/main Packages                               
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid/restricted Packages                         
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid/restricted Sources                          
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid/main Sources                                
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid/multiverse Sources                          
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid/universe Sources                            
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid/universe Packages                           
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid/multiverse Packages                         
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates/main Packages                       
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates/restricted Packages                 
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates/restricted Sources                  
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates/main Sources                        
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates/multiverse Sources                  
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates/universe Sources                    
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates/universe Packages                   
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-updates/multiverse Packages                 
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security/main Packages                      
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security/restricted Packages                
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security/restricted Sources                 
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security/main Sources                       
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security/multiverse Sources                 
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security/universe Sources                   
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security/universe Packages                  
Hit [http://ubuntu.osuosl.org](http://ubuntu.osuosl.org) lucid-security/multiverse Packages                
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Ign [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable/non-free Translation-en_US
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/dlynch3/ppa/ubuntu/](http://ppa.launchpad.net/dlynch3/ppa/ubuntu/) lucid/main Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu/](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ibus-dev/ibus-1.2-lucid/ubuntu/](http://ppa.launchpad.net/ibus-dev/ibus-1.2-lucid/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                            
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:4 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,203B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Fetched 7,045B in 20s (341B/s)                                                 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
chris@chris-laptop:~$



ok i notice  all the falures are gpg  and i got the files  that were missing aka ubuntu restricted extras among other media formats that i needed is there any way to  run synaptic  with that or no ?

---

### Post by michael_schmid on 2010-05-07
Seems like this is a known bug: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

OP: I suggest you check out the bug report and add yourself to the affected users.

---

### Post by iceman30ad on 2010-05-07
already have that  bug  report was shown to me in message 5 i beleave but im willing to  try anything to get this to  update and work right  about to try  reinstalling since i havent  my my stuff back on

---

### Post by michael_schmid on 2010-05-07
Sorry, I did not realize that the link to the bug report has already been posted. One thing you could always try is to temporarily disable the affected repositories, although you loose the ability to install software from said repositories. Just uncomment the affected repositories in /etc/apt/sources.list, using a '#' character.

Other than that I can't think of another solution than waiting for the bug fix.

---

### Post by pemadorje on 2010-05-07
Bug 574886 does seem to accurately describe this issue. I've tried different mirrors and get the same random errors. Iceman, I'm not sure if you mean that you are thinking about reinstalling Ubuntu Lucid, but if you are, I'd caution you about that. I've installed on two different machines and they both experience this issue. I also experimented last night by installing in VirtualBox to test and it also experiences this issue. So reinstalling may not solve your problem.

---

### Post by newb85 on 2010-05-17
I was experiencing a similar problem myself.

Unless you've already changed one of these settings, what's basically  happening is that NetworkManager is setting your router up as the DNS  server, and the router should use your ISP's DNS server to resolve  addresses.  Somewhere in there, addresses aren't all being resolved  correctly, hence "no address associated  with hostname".   If you want to see what's being used to resolve addresses, open  /etc/resolv.conf

NetworkManager can easily be set up to always use a manually-specified  DNS server when using a given network.  Under "Edit Connections..."  select the network where the issue is occurring (selecting the proper  tab at the top, if necessary), and click *Edit*.  Under the "IPv4  Settings" tab, set the *Method* to "Automatic (DHCP) addresses  only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

With any luck, this should solve your  problem.

---

### Post by iceman30ad on 2010-05-17
(insert unusual saying of disbelief)

that worked  and i got every thing  no questions asked


but it crashed the connection for every thing else

---

### Post by newb85 on 2010-05-18
> **iceman30ad said:**
> but it crashed the connection for every thing else

What do you mean is happening, exactly?

---

### Post by beyboo on 2010-05-18
This worked for me ! Thanks for posting

> **newb85 said:**
> I was experiencing a similar problem myself.

Unless you've already changed one of these settings, what's basically  happening is that NetworkManager is setting your router up as the DNS  server, and the router should use your ISP's DNS server to resolve  addresses.  Somewhere in there, addresses aren't all being resolved  correctly, hence "no address associated  with hostname".   If you want to see what's being used to resolve addresses, open  /etc/resolv.conf

NetworkManager can easily be set up to always use a manually-specified  DNS server when using a given network.  Under "Edit Connections..."  select the network where the issue is occurring (selecting the proper  tab at the top, if necessary), and click *Edit*.  Under the "IPv4  Settings" tab, set the *Method* to "Automatic (DHCP) addresses  only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

With any luck, this should solve your  problem.

---

### Post by pemadorje on 2010-05-18
@newb85

Your suggestion worked for me also. Thanks a ton!

---

### Post by iceman30ad on 2010-06-01
I must be an idiot  because the fix you gave us is working great for the others but not for me  if you could  supply screen shots and a walk through .... remember some newbs are smarter than others

---

### Post by pemadorje on 2010-06-01
Hi iceman,

I'll walk you through what I did. 

First you can set up a free account with OpenDNS (OpenDNS Basic) [http://www.opendns.com/start/]("http://www.opendns.com/start/")

Note: This is not mandatory but allows you to take full advantage of the OpenDNS security features. 

Then....


Step 1 - go to System &#8594; Preferences &#8594; Network Connections

Step 2 - Find either your wired or wireless network connection. Then select “edit”. Then go to the "IPv4 settings" tab.

Step 3 - Change “Method” to “Automatic (DHCP) addresses only” and enter OpenDNS's servers into the “DNS Servers” field. The IPs to enter are 208.67.222.222, 208.67.220.220. Hit "Apply" and you're all done. 




I've also attached screenshots of each step. Hope this helps.

---

### Post by iceman30ad on 2010-06-08
thanks a bunch  even i was able to get that (didnt know  about the open dns step i was trying the google one that was stated

---

### Post by Neilguy on 2010-06-11
That was great advice. Worked well for me too. Thanks a lot.:popcorn:

---

### Post by dr_smit on 2010-06-12
can any one explain what exactly has been suggested.. what are those dns addresses?

---

### Post by nixnine on 2010-06-15
I had been having the same problem with the "Something wicked" error.  This had happened as I tried to update through a wireless connection.  On advice, I connected though a wired connection and did an update.  Everything worked fine.  No "Wicked" errors.  Now, I can wireless connect and update with no problem.  It just took that one time to set everything right.

---

### Post by pyutaros on 2010-07-14
Entering Google (8.8.8.8) as my DNS erver worked for me.  AT&T Uverse customer with a 2Wire modem here.  Just one more reason I am not impressed with their service.

---

### Post by bcollignon on 2010-07-25
This worked!  I'm using OpenDNS along with Comcast Cablevision as my ISP and things started going south as soon as I switched from AT&T DSL.  Kudos!

> **newb85 said:**
> I was experiencing a similar problem myself.

Unless you've already changed one of these settings, what's basically  happening is that NetworkManager is setting your router up as the DNS  server, and the router should use your ISP's DNS server to resolve  addresses.  Somewhere in there, addresses aren't all being resolved  correctly, hence "no address associated  with hostname".   If you want to see what's being used to resolve addresses, open  /etc/resolv.conf

NetworkManager can easily be set up to always use a manually-specified  DNS server when using a given network.  Under "Edit Connections..."  select the network where the issue is occurring (selecting the proper  tab at the top, if necessary), and click *Edit*.  Under the "IPv4  Settings" tab, set the *Method* to "Automatic (DHCP) addresses  only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

With any luck, this should solve your  problem.

---

### Post by bcollignon on 2010-07-25
Here's a new look at things.  This is with screenshots which, I have found, gets to the quick of the matter.  Again, I can only say this works with OpenDNS which, up until I changed ISPs (AT&T to Comcast), worked fine without doing this.  However, the proof is in the pudding and it worked for me.  Mind you, I have OpenDNS servers listed within my router but, for whatever reason, Ubuntu seemed to want this solution for proper resolving of its repositories once Comcast came into the picture.  Go figure!

---

### Post by thefluffy on 2010-09-19
Does anyone know how to do this in Kubuntu? I have tried to change my router's DNS, but I still have the issues. I can change my /etc/resolv.conf and it fixes the issue. However, it resets after every reboot.

Thanks,

Daniel

---

### Post by anjupkg on 2010-09-24
i m having the same problem when i say:
apt-get update 
 i get the following error anyone can help please:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                                                                                
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
any one can suggest some good e-book on administration of ubuntu lucid lynx

---

### Post by ubrox on 2010-10-27
This works great! Although I dont understand how this should be a problem. trying to get to the failed address using a browser or ping works fine. I am not sure why a simple delay in DNS resolution should affect a user-level program. Even if it were a DNS resolution delay issue, re-running the command should not cause a repeat of the problem

> **newb85 said:**
> I was experiencing a similar problem myself.

Unless you've already changed one of these settings, what's basically  happening is that NetworkManager is setting your router up as the DNS  server, and the router should use your ISP's DNS server to resolve  addresses.  Somewhere in there, addresses aren't all being resolved  correctly, hence "no address associated  with hostname".   If you want to see what's being used to resolve addresses, open  /etc/resolv.conf

NetworkManager can easily be set up to always use a manually-specified  DNS server when using a given network.  Under "Edit Connections..."  select the network where the issue is occurring (selecting the proper  tab at the top, if necessary), and click *Edit*.  Under the "IPv4  Settings" tab, set the *Method* to "Automatic (DHCP) addresses  only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

With any luck, this should solve your  problem.

---

### Post by wobbe on 2010-12-14
This worked for me also in Linux Mint 10
Thank you!

---

### Post by fallenshadow on 2010-12-28
> Under "Edit Connections..." select the network where the issue is occurring (selecting the proper tab at the top, if necessary), and click Edit. Under the "IPv4 Settings" tab, set the Method to "Automatic (DHCP) addresses only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

Thanks so much for this valuble information! Works under Ubuntu 10.10 too. :)

---

### Post by bwalton on 2011-02-26
This fix worked for me on two out of two Ubuntu laptops I have.  Thanks much!

---

### Post by deoanam2002 on 2012-02-03
In Ubuntu Studio 10.10, I went to System->Administration->Network and in the DNS tab simply added 8.8.8.8.
I was then able to do apt-get update successfully. Not sure yet if this is going to have any adverse effects. Thanks for this!

---

### Post by pawanmup on 2012-05-10
n Ubuntu 10.04, I went to System->Preference->Network Connections and in the DNS Servers tab added 208.67.222.222, 208.67.220.220

and did apt-get update but no luck, got below update please help


# apt-get update
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) lucid Release.gpg
  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US       
  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

---

### Post by iceman30ad on 2012-05-22
just use one it goes schioid when you use two and i get better results with wicd rather than network manager

---

