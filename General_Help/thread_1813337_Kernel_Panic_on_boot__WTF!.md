---
title: "Kernel Panic on boot?  WTF!?"
date: 2011-07-27
forum: General Help
---

### Post by T3kG33k on 2011-07-27
I just began receiving this error on boot not terribly long ago and I've been googling the crap out of it only to come up short :(

I've heard that it's caused by bad RAM and I've scanned mine with memtest only to come back clean!

I have a feeling that this issue is caused by initrd/ initram but I'm not the best at trouble shooting start up errors.  I'm not really sure where the log file is for start up.

Some guidance would be appreciated.

PS.  I can switch back to kernel 2.6.35-27 generic and everything works fine.  Anything after that comes up with the same error.

---

### Post by lkjoel on 2011-07-27
> **T3kG33k said:**
> I just began receiving this error on boot not terribly long ago and I've been googling the crap out of it only to come up short :(

I've heard that it's caused by bad RAM and I've scanned mine with memtest only to come back clean!

I have a feeling that this issue is caused by initrd/ initram but I'm not the best at trouble shooting start up errors.  I'm not really sure where the log file is for start up.

Some guidance would be appreciated.

PS.  I can switch back to kernel 2.6.35-27 generic and everything works fine.  Anything after that comes up with the same error.
Could you give me the output of:
```
lsb_release -a
uname -a

```
Then try this:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by T3kG33k on 2011-07-27
Sure thing

Output of lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

Output of uname -a

Linux MobileToolKit 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux

Output of sudo apt-get update

Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick Release.gpg
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/main Translation-en              
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/main Translation-en_US           
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/multiverse Translation-en        
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/multiverse Translation-en_US     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/restricted Translation-en        
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/restricted Translation-en_US     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/universe Translation-en          
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/universe Translation-en_US       
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates Release.gpg                      
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/main Translation-en      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/main Translation-en_US   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/) maverick/main Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/) maverick/main Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/universe Translation-en  
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security Release.gpg                     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/main Translation-en     
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/main Translation-en_US  
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/restricted Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/universe Translation-en 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/conky-companions/ppa/ubuntu/](http://ppa.launchpad.net/conky-companions/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/conky-companions/ppa/ubuntu/](http://ppa.launchpad.net/conky-companions/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed Release.gpg                     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/main Translation-en     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/main Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/multiverse Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,351B]                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                      
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/universe Translation-en 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/universe Translation-en_US
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick Release  
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates Release
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security Release
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed Release               
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,264B]        
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/restricted Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/main Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/multiverse Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/universe Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/main i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/restricted i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/universe i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/multiverse i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/restricted Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/main Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/multiverse Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/universe Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/main i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/restricted i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/universe i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/multiverse i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/restricted Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/main Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/multiverse Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/universe Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/main i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/restricted i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/universe i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/multiverse i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed/restricted i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed/main i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed/multiverse i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed/universe i386 Packages

Output of sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

thanks for the reply!

---

### Post by lkjoel on 2011-07-27
Could you give me the output of this:
```
sudo add-apt-repository ppa:lkjoel/apt-undo && sudo apt-get update; sudo apt-get install apt-undo
apt-undo purge linux-headers-`uname -r` linux-image-`uname -r`
apt-undo undo

```

---

### Post by T3kG33k on 2011-07-27
Output of sudo add-apt-repository ppa:lkjoel/apt-undo && sudo apt-get update; sudo apt-get install apt-undo

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B5BA6675C3C7E882049C5A0C20B1405FC2255669
gpg: requesting key C2255669 from hkp server keyserver.ubuntu.com
^C
gpg: Interrupt caught ... exiting
Exception KeyboardInterrupt in <module 'threading' from '/usr/lib/python2.6/threading.pyc'> ignored
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick Release.gpg
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/main Translation-en              
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/main Translation-en_US           
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/multiverse Translation-en        
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/multiverse Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/) maverick/main Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/restricted Translation-en        
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/restricted Translation-en_US     
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/conky-companions/ppa/ubuntu/](http://ppa.launchpad.net/conky-companions/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/conky-companions/ppa/ubuntu/](http://ppa.launchpad.net/conky-companions/ppa/ubuntu/) maverick/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/](http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/](http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/) maverick/main Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/universe Translation-en          
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick/universe Translation-en_US       
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates Release.gpg                      
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/main Translation-en      
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/main Translation-en_US   
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,745B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/universe Translation-en  
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security Release.gpg                     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/main Translation-en     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/main Translation-en_US  
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/restricted Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/universe Translation-en 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed Release.gpg                     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/main Translation-en     
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/main Translation-en_US  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex             
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-proposed/universe Translation-en_US
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick Release                             
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates Release                     
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security Release                    
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed Release                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/restricted Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/main Sources  
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/multiverse Sources                  
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/universe Sources                    
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/main i386 Packages                  
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/restricted i386 Packages            
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/universe i386 Packages              
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick/multiverse i386 Packages            
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/restricted Sources          
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/main Sources                
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/multiverse Sources          
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/universe Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                 
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/main i386 Packages          
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/restricted i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/universe i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-updates/multiverse i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/restricted Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/main Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/multiverse Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/universe Sources
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/main i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/restricted i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/universe i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-security/multiverse i386 Packages
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed/restricted i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed/main i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed/multiverse i386 Packages
Hit [http://mirror.cs.umn.edu](http://mirror.cs.umn.edu) maverick-proposed/universe i386 Packages
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,351B]
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,264B]
Fetched 3,130B in 5s (615B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 20B1405FC2255669
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-25 linux-headers-2.6.35-25-generic postgresql-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  apt-undo
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,890B of archives.
After this operation, 45.1kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  apt-undo
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/](http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/) maverick/main apt-undo all 0.1.3-2~maverick1 [2,890B]
Fetched 2,890B in 0s (4,948B/s)   
Selecting previously deselected package apt-undo.
(Reading database ... 296063 files and directories currently installed.)
Unpacking apt-undo (from .../apt-undo_0.1.3-2~maverick1_all.deb) ...
Setting up apt-undo (0.1.3-2~maverick1) ...


Output of apt-undo purge linux-headers-`uname -r` linux-image-`uname -r`

/usr/bin/apt-undo: line 26: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-25 linux-headers-2.6.35-25-generic postgresql-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-2.6.35-27-generic* linux-image-2.6.35-27-generic*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 117MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 296067 files and directories currently installed.)
Removing linux-headers-2.6.35-27-generic ...
Removing linux-image-2.6.35-27-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-2.6.35-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
Creating undo data ... 
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
/usr/bin/apt-undo: line 38: /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
sed: can't read /home/nick/.aptundo/2011/07/27/2007/27/2011160415: No such file or directory
chmod: cannot access `/home/nick/.aptundo/2011/07/27/2007/27/2011160415': No such file or directory
cp: cannot stat `/home/nick/.aptundo/2011/07/27/2007/27/2011160415': No such file or directory
chmod: cannot access `/home/nick/.aptundo/lastundo': No such file or directory
To undo: bash /home/nick/.aptundo/2011/07/27/2007/27/2011160415

Output of apt-undo undo

bash: /home/nick/.aptundo/lastundo: No such file or directory

---

### Post by sbraz on 2011-07-27
do you have a separate /boot partition?

anyhow try this:

sudo update-initramfs -uk all
sudo update-grub

---

### Post by lkjoel on 2011-07-27
Now type this in the Terminal window:
```
sudo apt-get install linux-headers-2.6.35-27-generic linux-image-2.6.35-27-generic

```

---

### Post by T3kG33k on 2011-07-27
> **sbraz said:**
> do you have a separate /boot partition?

anyhow try this:

sudo update-initramfs -uk all
sudo update-grub

I do not have a separate boot partition.

Outout for sudo update-initramfs -uk all

update-initramfs: Generating /boot/initrd.img-2.6.35-30-generic
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic


Output for sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by T3kG33k on 2011-07-27
> **lkjoel said:**
> Now type this in the Terminal window:
```
sudo apt-get install linux-headers-2.6.35-27-generic linux-image-2.6.35-27-generic

```

Out put

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-25 linux-headers-2.6.35-25-generic postgresql-common
Use 'apt-get autoremove' to remove them.
Suggested packages:
  fdutils linux-doc-2.6.35 linux-source-2.6.35 linux-tools
The following NEW packages will be installed:
  linux-headers-2.6.35-27-generic linux-image-2.6.35-27-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.7MB of archives.
After this operation, 117MB of additional disk space will be used.
Get:1 [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/main linux-image-2.6.35-27-generic i386 2.6.35-27.48 [33.9MB]
Get:2 [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) maverick-updates/main linux-headers-2.6.35-27-generic i386 2.6.35-27.48 [792kB]
Fetched 34.7MB in 5min 33s (104kB/s)                                           
Selecting previously deselected package linux-image-2.6.35-27-generic.
(Reading database ... 284900 files and directories currently installed.)
Unpacking linux-image-2.6.35-27-generic (from .../linux-image-2.6.35-27-generic_2.6.35-27.48_i386.deb) ...
Done.
Selecting previously deselected package linux-headers-2.6.35-27-generic.
Unpacking linux-headers-2.6.35-27-generic (from .../linux-headers-2.6.35-27-generic_2.6.35-27.48_i386.deb) ...
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-headers-2.6.35-27-generic (2.6.35-27.48) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic

---

### Post by lkjoel on 2011-07-27
Now type in the Terminal window:
```
sudo apt-get update
sudo apt-get dist-upgrade
apt-undo purge linux-image-2.6.35-30-generic linux-headers-2.6.35-30-generic
apt-undo undo

```

---

### Post by T3kG33k on 2011-07-27
Well I'm boned now.  I briefly lost power at my building and my laptop shut down.  I've got a kernel list at grub but now I can't boot to any of them.

Darn :,(

---

### Post by lkjoel on 2011-07-27
> **T3kG33k said:**
> Well I'm boned now.  I briefly lost power at my building and my laptop shut down.  I've got a kernel list at grub but now I can't boot to any of them.

Darn :,(
You have 2 options now: Reinstall Ubuntu from scratch, or use a Rescue Live CD, and chroot into the broken system. I can help you with both if you need help.

---

### Post by T3kG33k on 2011-07-27
I think I'll just re-install from scratch.  It's about that time anyway.  Got any tips on backing up a user profile and some apps?

I've got an external hard drive adapter.

---

### Post by lkjoel on 2011-07-27
> **T3kG33k said:**
> I think I'll just re-install from scratch.  It's about that time anyway.  Got any tips on backing up a user profile and some apps?

I've got an external hard drive adapter.
Get a Rescue LiveCD, and from that, copy and paste your home folder into the external hard drive.

For the apps, I don't know how, except to use AptonCD to install your apps on a CD, and then on the new system, install what's on the CD

---

