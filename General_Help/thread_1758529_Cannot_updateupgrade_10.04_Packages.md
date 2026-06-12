---
title: "Cannot update/upgrade 10.04 Packages"
date: 2011-05-14
forum: General Help
---

### Post by crits on 2011-05-14
I am attempting to patch an Ubuntu 10.04 system.

When I log in, I get these two informative messages 

```
95 packages can be updated.
55 updates are security updates.
```

However, when I run apt-get update and apt-get upgrade this is the result:

```
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                                                          
Ign http://ppa.launchpad.net/ssakar/ppa/ubuntu/ lucid/main Translation-en_US                                            
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                 
Hit http://us.archive.ubuntu.com lucid Release.gpg                                                                                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                                          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                                                                    
Hit http://security.ubuntu.com lucid-security Release.gpg                                                                
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                                             
Hit http://archive.canonical.com lucid Release                                                                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                              
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                                                               
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                            
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                        
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                      
Hit http://us.archive.ubuntu.com lucid Release                                                                           
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ lucid/main Translation-en_US                                    
Hit http://ppa.launchpad.net lucid Release                                                                               
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                                                                     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                               
Hit http://security.ubuntu.com lucid-security Release                                      
Hit http://ppa.launchpad.net lucid Release                                                                       
Hit http://us.archive.ubuntu.com lucid-updates Release                                                                                 
Hit http://archive.canonical.com lucid/partner Packages                                                                                
Hit http://security.ubuntu.com lucid-security/main Packages                                                                            
Hit http://ppa.launchpad.net lucid/main Packages                                           
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://us.archive.ubuntu.com lucid/restricted Packages           
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://ppa.launchpad.net lucid/main Sources                      
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources           
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages     
Hit http://archive.scrapy.org lucid-0.9 Release.gpg                  
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

When I attempt to do the same thing using Synaptic, it shows that it's downloading 0 bytes from all the repositories when updating.

I'm ashamed to say that this machine hasn't been updated in quite some time, so there are *definitely* things to download.

---

### Post by plucky on 2011-05-14
Try this [Link](http://ubuntuforums.org/showthread.php?t=1737467)

Good Luck

---

### Post by crits on 2011-05-14
Yep, deleting motd.tail fixed the issue.

I was just seeing an outdated message.

However I'm still concerned that there hasn't been any updates since my last upgrade...

I'll try changing mirrors.

---

