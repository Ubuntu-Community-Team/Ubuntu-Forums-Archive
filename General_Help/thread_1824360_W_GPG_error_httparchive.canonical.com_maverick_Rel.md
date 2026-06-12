---
title: "W: GPG error: http://archive.canonical.com maverick Release"
date: 2011-08-13
forum: General Help
---

### Post by techbrainless on 2011-08-13
Hi All,
When trying to execute the apt-get update i got the following error

```
test@test-pc:~$ sudo apt-get update --fix-broken --fix-missing 
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ maverick/main Translation-en_US
Hit http://download.virtualbox.org maverick Release.gpg                        
Get:1 http://archive.canonical.com maverick Release.gpg [198B]                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://sa.archive.ubuntu.com maverick Release.gpg                          
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en_US
Hit http://archive.canonical.com maverick Release                              
Ign http://archive.canonical.com maverick Release                              
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://sa.archive.ubuntu.com maverick-updates Release.gpg                  
Hit http://download.virtualbox.org maverick Release                            
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex      
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://download.virtualbox.org maverick/contrib i386 Packages              
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://sa.archive.ubuntu.com maverick Release
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates Release
Hit http://sa.archive.ubuntu.com maverick/main Sources
Hit http://sa.archive.ubuntu.com maverick/restricted Sources
Hit http://sa.archive.ubuntu.com maverick/universe Sources
Hit http://sa.archive.ubuntu.com maverick/multiverse Sources
Hit http://sa.archive.ubuntu.com maverick/main i386 Packages
Hit http://sa.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://sa.archive.ubuntu.com maverick/universe i386 Packages
Hit http://sa.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/main Sources
Hit http://sa.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://sa.archive.ubuntu.com maverick-updates/universe Sources
Hit http://sa.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://sa.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 198B in 5s (34B/s)
Reading package lists... Done
W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
test@test-pc:~$ sudo apt-get update --fix-broken --fix-missing 
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Get:1 http://archive.canonical.com maverick Release.gpg [198B]                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://download.virtualbox.org maverick Release.gpg                        
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://sa.archive.ubuntu.com maverick Release.gpg                          
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en_US
Hit http://archive.canonical.com maverick Release                              
Ign http://archive.canonical.com maverick Release                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://security.ubuntu.com maverick-security Release                       
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
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex      
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://sa.archive.ubuntu.com maverick Release                              
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://download.virtualbox.org maverick/contrib i386 Packages              
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates Release
Hit http://sa.archive.ubuntu.com maverick/main Sources
Hit http://sa.archive.ubuntu.com maverick/restricted Sources
Hit http://sa.archive.ubuntu.com maverick/universe Sources
Hit http://sa.archive.ubuntu.com maverick/multiverse Sources
Hit http://sa.archive.ubuntu.com maverick/main i386 Packages
Hit http://sa.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://sa.archive.ubuntu.com maverick/universe i386 Packages
Hit http://sa.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/main Sources
Hit http://sa.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://sa.archive.ubuntu.com maverick-updates/universe Sources
Hit http://sa.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://sa.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 198B in 5s (35B/s)
Reading package lists... Done
W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
test@test-pc:~$ sudo apt-get update --fix-broken --fix-missing 
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/ maverick/main Translation-en_US
Get:1 http://archive.canonical.com maverick Release.gpg [198B]                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://download.virtualbox.org maverick Release.gpg                        
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://sa.archive.ubuntu.com maverick Release.gpg                          
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en_US
Hit http://archive.canonical.com maverick Release                              
Ign http://archive.canonical.com maverick Release                              
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://security.ubuntu.com maverick-security Release                       
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
Hit http://download.virtualbox.org maverick Release                            
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://sa.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://download.virtualbox.org maverick/contrib i386 Packages              
Hit http://sa.archive.ubuntu.com maverick Release                              
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates Release
Hit http://sa.archive.ubuntu.com maverick/main Sources
Hit http://sa.archive.ubuntu.com maverick/restricted Sources
Hit http://sa.archive.ubuntu.com maverick/universe Sources
Hit http://sa.archive.ubuntu.com maverick/multiverse Sources
Hit http://sa.archive.ubuntu.com maverick/main i386 Packages
Hit http://sa.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://sa.archive.ubuntu.com maverick/universe i386 Packages
Hit http://sa.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/main Sources
Hit http://sa.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://sa.archive.ubuntu.com maverick-updates/universe Sources
Hit http://sa.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://sa.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://sa.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 198B in 5s (34B/s)
Reading package lists... Done
W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
test@test-pc:~$ 

```

---

### Post by techbrainless on 2011-08-13
I have commited the following line @sources.list
```
deb http://archive.canonical.com/ubuntu maverick partner
```
and it works fine for me.

---

