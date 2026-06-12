---
title: "apt, PPA, or driver broken?"
date: 2011-09-28
forum: General Help
---

### Post by yuler on 2011-09-28
Not sure how to fix this problem [installing a Wacom]("http://www.ubuntugeek.com/install-the-wacom-bamboo-driver-in-ubuntu-10-04-lucid-lynx-using-ppas.html") driver.  Help?

```
yuler@nodeal:~$ sudo add-apt-repository ppa:doctormo/wacom-plus
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv C7B9C50274F4E032B70AB2EA15A579BF113659DF
gpg: requesting key 113659DF from hkp server keyserver.ubuntu.com
gpg: key 113659DF: "Launchpad PPA for Martin Owens" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

Hmm.  Didn't realize I'd already the PPA.  Since it checked out, I burrowed on.

```

yuler@nodeal:~$ sudo apt-get update

Hit http://archive.canonical.com maverick Release.gpg                          
Hit http://extras.ubuntu.com maverick Release.gpg     
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Hit http://ubuntu.mirror.cambrium.nl maverick Release.gpg                      
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Hit http://packages.medibuntu.org maverick Release.gpg                         
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick/main Translation-en      
Ign http://deb.opera.com/opera/ stable/non-free Translation-en                 
Ign http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick/main Translation-en_US   
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/ maverick/main Translation-en_US
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://archive.canonical.com maverick Release                              
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick/universe Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Hit http://deb.opera.com stable Release                                        
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick/universe Translation-en_US
Hit http://archive.getdeb.net maverick-getdeb Release.gpg                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://deb.opera.com stable/non-free i386 Packages                         
Ign http://osiris.kodeware.net stable Release.gpg                              
Ign http://ppa.launchpad.net/george-edison55/george-edison/ubuntu/ maverick/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US         
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en      
Hit http://archive.canonical.com maverick/partner i386 Packages                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://ubuntu.mirror.cambrium.nl maverick Release                          
Ign http://deb.opera.com stable/non-free i386 Packages                         
Ign http://ppa.launchpad.net/george-edison55/george-edison/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://osiris.kodeware.net/repository/debian/ stable/non-free Translation-en
Hit http://packages.medibuntu.org maverick Release                             
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en_US   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Hit http://ubuntu.mirror.cambrium.nl maverick/main Sources                     
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://osiris.kodeware.net/repository/debian/ stable/non-free Translation-en_US
Hit http://packages.medibuntu.org maverick/free i386 Packages                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Hit http://ubuntu.mirror.cambrium.nl maverick/universe Sources                 
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://ubuntu.mirror.cambrium.nl maverick/main i386 Packages               
Hit http://packages.medibuntu.org maverick/non-free i386 Packages              
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Hit http://ubuntu.mirror.cambrium.nl maverick/universe i386 Packages           
Hit http://archive.getdeb.net maverick-getdeb Release                          
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://osiris.kodeware.net stable Release                                  
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://archive.getdeb.net maverick-getdeb/apps i386 Packages               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://osiris.kodeware.net stable/non-free i386 Packages/DiffIndex         
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Ign http://ppa.launchpad.net/matthaeus123/ppa/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Ign http://ppa.launchpad.net/matthaeus123/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://osiris.kodeware.net stable/non-free i386 Packages                   
Hit http://us.archive.ubuntu.com maverick Release                              
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick/main Sources                         
Ign http://osiris.kodeware.net stable/non-free i386 Packages                   
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://us.archive.ubuntu.com maverick/restricted Sources                   
Ign http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick/universe Sources                     
Ign http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/ maverick/main Translation-en_US
Hit http://osiris.kodeware.net stable/non-free i386 Packages                   
Hit http://us.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://ppa.launchpad.net maverick Release.gpg                             
Hit http://us.archive.ubuntu.com maverick/main i386 Packages               
Ign http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages         
Ign http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages           
Hit http://ppa.launchpad.net maverick Release.gpg                             
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages         
Ign http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages 
Ign http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages       
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Hit http://ppa.launchpad.net maverick Release.gpg                             
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages       
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg    
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release        
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick/main Sources                         
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources   
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Reading package lists... Done

```

What do the repeating hits on maverick mean?  

```

yuler@nodeal:~$ sudo apt-get install wacom-dkms xf86-input-wacom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xf86-input-wacom
yuler@nodeal:~$
```

Oh, that's great.  Does the PPA not exist?  Does the file(s) at the PPA not exist?  Did it fail during download?  Is it corrupt?  How do I diagnose this?

---

### Post by dcstar on 2011-09-28
> **yuler said:**
> 
..........
Oh, that's great.  Does the PPA not exist?  **Does the file(s) at the PPA not exist?**  Did it fail during download?  Is it corrupt?  How do I diagnose this?

Why don't **you** go to the PPA site and see for yourself?

---

### Post by yuler on 2011-09-28
That would fall under the "how do I diagnose this" category.  I'm a long way from understanding how Linux works.

So, I found the URL embedded by editing "software sources" and found a folder list of CPU releases.  Looks as if packages are archived files, but inside the i386 archive, there was only a text file that explained what the purpose is.  OK, but doesn't help particular problem.

I could toil to figure out how to diagnose this, but surely someone has done it already and written about it.

---

