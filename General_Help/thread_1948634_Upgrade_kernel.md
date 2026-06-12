---
title: "Upgrade kernel"
date: 2012-03-28
forum: General Help
---

### Post by techbrainless on 2012-03-28
Hi All,
I am trying to upgrade from (ubuntu 10.04) kernel 2.6.35-30-generic to kernel 2.6.38


I have executed the commands mentioned at the link [http://ubuntuguide.net/ppa-of-linux-backport-natty-2-6-38-10-46-for-ubuntu-10-04-lucid]("http://ubuntuguide.net/ppa-of-linux-backport-natty-2-6-38-10-46-for-ubuntu-10-04-lucid")

but getting the following errors

```

user1@testmachine:/var/lib/apt/lists$ sudo add-apt-repository ppa:euroford/linux-kernel
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv BAB86065B69A0230628C9A203655FD82B22BBE45
gpg: requesting key B22BBE45 from hkp server keyserver.ubuntu.com
gpg: key B22BBE45: "Launchpad PPA for An Yang" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
user1@testmachine:/var/lib/apt/lists$ sudo apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg                                                                                                                                                                
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                  
Hit http://download.virtualbox.org maverick Release.gpg                                                                               
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                        
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ lucid/main Translation-en                                                         
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ lucid/main Translation-en_US                                                       
Hit http://archive.canonical.com maverick Release.gpg                                                                                  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                               
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US                                                            
Hit http://security.ubuntu.com maverick-security Release.gpg                                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US                                                        
Hit http://sa.archive.ubuntu.com maverick Release.gpg                                                                                  
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                  
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                               
Hit http://extras.ubuntu.com maverick Release                                                                                          
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en                                                  
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en_US                         
Ign http://ppa.launchpad.net maverick Release.gpg                                                                
Ign http://ppa.launchpad.net/euroford/linux-kernel/ubuntu/ maverick/main Translation-en                          
Ign http://ppa.launchpad.net/euroford/linux-kernel/ubuntu/ maverick/main Translation-en_US                       
Hit http://ppa.launchpad.net maverick Release.gpg                                                                
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ maverick/main Translation-en                                 
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ maverick/main Translation-en_US                              
Hit http://ppa.launchpad.net maverick Release.gpg                                                                
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ maverick/main Translation-en                                             
Hit http://archive.canonical.com maverick Release                                                                                                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                                                 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US                                                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US                                                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                                             
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                                                                                      
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                                                                                                                   
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                                                                                                      
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                                                                                                                   
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                                                                  
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                                                                                               
Hit http://sa.archive.ubuntu.com maverick-updates Release.gpg                                                                                                              
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                                                                                    
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                                                                                                                 
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                                                                                              
Hit http://extras.ubuntu.com maverick/main Sources                                                                                                                                               
Hit http://download.virtualbox.org maverick Release                                                                                                                                              
Hit http://archive.canonical.com maverick/partner i386 Packages                                                                                                                                  
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US                                                                                     
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                              
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US                           
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US                             
Hit http://sa.archive.ubuntu.com maverick Release                                                                
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                                               
Hit http://download.virtualbox.org maverick/contrib i386 Packages                                                                      
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ maverick/main Translation-en_US                    
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release             
Hit http://sa.archive.ubuntu.com maverick-updates Release            
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                           
Ign http://ppa.launchpad.net maverick Release                        
Hit http://ppa.launchpad.net maverick Release                                              
Hit http://ppa.launchpad.net maverick Release                                              
Hit http://ppa.launchpad.net maverick Release                                              
Hit http://security.ubuntu.com maverick-security/main Sources                              
Hit http://sa.archive.ubuntu.com maverick/main Sources               
Hit http://sa.archive.ubuntu.com maverick/restricted Sources         
Hit http://sa.archive.ubuntu.com maverick/universe Sources           
Hit http://sa.archive.ubuntu.com maverick/multiverse Sources         
Hit http://sa.archive.ubuntu.com maverick/main i386 Packages         
Hit http://sa.archive.ubuntu.com maverick/restricted i386 Packages   
Ign http://ppa.launchpad.net maverick/main Sources                   
Ign http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://ppa.launchpad.net lucid/main Sources                      
Hit http://ppa.launchpad.net lucid/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources    
Hit http://security.ubuntu.com maverick-security/multiverse Sources  
Hit http://security.ubuntu.com maverick-security/main i386 Packages  
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://sa.archive.ubuntu.com maverick/universe i386 Packages     
Hit http://sa.archive.ubuntu.com maverick/multiverse i386 Packages   
Hit http://sa.archive.ubuntu.com maverick-updates/main Sources       
Hit http://sa.archive.ubuntu.com maverick-updates/restricted Sources 
Hit http://sa.archive.ubuntu.com maverick-updates/universe Sources   
Hit http://sa.archive.ubuntu.com maverick-updates/multiverse Sources 
Hit http://sa.archive.ubuntu.com maverick-updates/main i386 Packages 
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://ppa.launchpad.net maverick/main i386 Packages
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/euroford/linux-kernel/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/euroford/linux-kernel/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
user1@testmachine:/var/lib/apt/lists$ sudo apt-get install linux-image-2.6.38-10-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-2.6.38-10-generic
E: Couldn't find any package by regex 'linux-image-2.6.38-10-generic'
user1@testmachine:/var/lib/apt/lists$ 

```

---

### Post by QIII on 2012-03-28
The first thing that strikes me is that four of your urls are not found (404), which means they have either moved or been taken down.

If your tutorial is set up for you to find the kernel in one of those PPAs, it will fail.

---

### Post by snowpine on 2012-03-28
10.10 reaches its "end of life" in a month, so the PPA's are starting to dry up.

Easiest way to get the kernel you want is just go here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Find your desired kernel and click the correct linux-image .deb for your architecture (i386 or amd64) to download, then install with Gdebi.

---

### Post by Manyette on 2012-03-28
Snowpine:
Thanks very much.  I've been trying to figure out how to do this for months, and you made it so simple! I am very grateful.  Thank you

---

