---
title: "Negative-sized nonexistent package"
date: 2010-09-04
forum: General Help
---

### Post by HyperHacker on 2010-09-04
Something about this strikes me as not making any sense:> $ apt-cache search synergy|grep synergy
quicksynergy - GUI for easy configuration of Synergy
synergy-plus - Installs Synergy+ server and client
synergy - Share mouse, keyboard and clipboard over the network

$ sudo apt-get remove synergy-plus
[sudo] password for hyperhacker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  synergy-plus
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 479MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 182471 files and directories currently installed.)
Removing synergy-plus ...

$ sudo apt-get install synergy-plus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package synergy-plus

$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_CA              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_CA
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_CA              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg             
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages              
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages              
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA [10.3kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA [425B]
Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA [663B]
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed Release.gpg                    
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_CA 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release                                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed Release                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed/restricted Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed/main Packages                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed/multiverse Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-proposed/universe Packages              
Fetched 11.4kB in 35s (322B/s)                                                 
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

$ apt-cache search synergy|grep synergy
quicksynergy - GUI for easy configuration of Synergy
synergy - Share mouse, keyboard and clipboard over the networkHow does removing this package use up 479MB, and now it no longer exists?

I'm also getting a lot of warnings lately that packages can't be authenticated, even from automatic updates. If I wait long enough (sometimes a few minutes, sometimes over 24 hours) and try installing again, I don't get the warning anymore, as if it's taking a very long time to download authentication data?

---

### Post by dcstar on 2010-09-04
> **HyperHacker said:**
> 
........
I'm also getting a lot of warnings lately that packages can't be authenticated, even from automatic updates. If I wait long enough (sometimes a few minutes, sometimes over 24 hours) and try installing again, I don't get the warning anymore, as if it's taking a very long time to download authentication data?

Do not use default repositories, manually select one close to your location or use the "Auto" facility to find one.

---

