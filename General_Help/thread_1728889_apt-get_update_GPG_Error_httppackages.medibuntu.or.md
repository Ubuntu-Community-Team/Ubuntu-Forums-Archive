---
title: "apt-get update GPG Error http://packages.medibuntu.org maverick"
date: 2011-04-14
forum: General Help
---

### Post by Rocket J Squirrel on 2011-04-14
apt-get update found something it didn't like about [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick so it didn't run. I've pasted all output below, the error is at the tail, but maybe there's something relevant midway down? 

```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get update
[sudo] password for jackelliott: 
Get:1 http://dl.google.com stable Release.gpg [197B]                                                                                                        
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                                                       
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US                                                                                    
Get:2 http://dl.google.com stable Release.gpg [197B]                                                                                                        
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                                                   
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US                                                                                
Get:3 http://dl.google.com stable Release [1,347B]                                                                                                          
Get:4 http://dl.google.com stable Release [1,347B]                                                                                                          
Get:5 http://dl.google.com stable/main i386 Packages [1,082B]                                                                                               
Get:6 http://dl.google.com stable/main i386 Packages [737B]                                                                                                 
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                           
Ign http://ppa.launchpad.net/claws-mail/ppa/ubuntu/ maverick/main Translation-en                                                                            
Ign http://ppa.launchpad.net/claws-mail/ppa/ubuntu/ maverick/main Translation-en_US                                                                         
Hit http://us.archive.ubuntu.com maverick Release.gpg                                                                                                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                                    
Hit http://extras.ubuntu.com maverick Release.gpg                                                                                                           
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                           
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                                        
Hit http://archive.canonical.com maverick Release.gpg                                                                                                       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                               
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US                                                                                 
Hit http://security.ubuntu.com maverick-security Release.gpg                                                                                                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                                                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US                                                                             
Get:7 http://packages.medibuntu.org maverick Release.gpg [197B]                                                                                             
Get:8 http://download.tuxfamily.org  Release.gpg [198B]                                                                                                     
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                           
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en                                                                 
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en_US                                                              
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                           
Ign http://ppa.launchpad.net/kilian/f.lux/ubuntu/ maverick/main Translation-en                                                                              
Ign http://ppa.launchpad.net/kilian/f.lux/ubuntu/ maverick/main Translation-en_US                                                                           
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                                                                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                                                                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                                                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                                                                                
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                                                                                               
Hit http://extras.ubuntu.com maverick Release                                                                                                               
Hit http://archive.canonical.com maverick Release                                                                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                                          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US                                                                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                                                          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US                                                                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                                                            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US                                                                         
Hit http://security.ubuntu.com maverick-security Release                                                                                                    
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en                                                                           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                                               
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en                                                                                      
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en_US                                                                                   
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_US                                                                        
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                                                                            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                                                         
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                                                                    
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en                                                                
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US                                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                                                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US                                                   
Hit http://us.archive.ubuntu.com maverick Release                                                                                      
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                      
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en                                                      
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en_US                                                   
Ign http://packages.medibuntu.org/ maverick/free Translation-en                                                                                             
Hit http://archive.canonical.com maverick/partner Sources                                                                              
Get:9 http://download.tuxfamily.org  Release [724B]                                                                                               
Hit http://security.ubuntu.com maverick-security/main Sources                                                                                               
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                           
Ign http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ maverick/main Translation-en                                                    
Ign http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ maverick/main Translation-en_US                                                           
Hit http://ppa.launchpad.net maverick Release                                                                                                               
Hit http://ppa.launchpad.net maverick Release                                                                                                               
Hit http://us.archive.ubuntu.com maverick-updates Release                                                                                                   
Hit http://archive.canonical.com maverick/partner i386 Packages                                                                                             
Hit http://security.ubuntu.com maverick-security/restricted Sources                                                                                         
Hit http://security.ubuntu.com maverick-security/universe Sources                                                                                           
Hit http://security.ubuntu.com maverick-security/multiverse Sources                                                                    
Hit http://security.ubuntu.com maverick-security/main i386 Packages                                                                    
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages                                                              
Hit http://security.ubuntu.com maverick-security/universe i386 Packages                                                                
Ign http://download.tuxfamily.org  Packages                                                                                            
Hit http://us.archive.ubuntu.com maverick/main Sources                                                           
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://us.archive.ubuntu.com maverick/restricted Sources                                                                           
Hit http://us.archive.ubuntu.com maverick/universe Sources                                                                             
Hit http://us.archive.ubuntu.com maverick/multiverse Sources                                                                           
Hit http://us.archive.ubuntu.com maverick/main i386 Packages                                                                           
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages                                                                     
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages                                                                       
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages                                                              
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US                                               
Ign http://download.tuxfamily.org  Packages                                                                                                       
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages                                                          
Hit http://ppa.launchpad.net maverick/main Sources                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                    
Hit http://ppa.launchpad.net maverick/main Sources                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                    
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                                                              
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources                                                        
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources                                                          
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources                                                        
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages                                                        
Get:10 http://download.tuxfamily.org  Packages [8,362B]                                                                     
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages                                                  
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages                             
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages                           
Hit http://ppa.launchpad.net maverick/main Sources                                                   
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Hit http://ppa.launchpad.net maverick/main Sources                                                              
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                        
Hit http://ppa.launchpad.net maverick/main Sources                                                              
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                        
Hit http://ppa.launchpad.net maverick/main Sources                                                              
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                        
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US          
Get:11 http://packages.medibuntu.org maverick Release [6,860B]
Ign http://packages.medibuntu.org maverick Release        
Ign http://packages.medibuntu.org maverick/free i386 Packages/DiffIndex
Ign http://packages.medibuntu.org maverick/non-free i386 Packages/DiffIndex
Hit http://packages.medibuntu.org maverick/free i386 Packages
Hit http://packages.medibuntu.org maverick/non-free i386 Packages
Fetched 14.4kB in 4s (2,981B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

Update Manager ran fine. Any ideas?

---

### Post by WorMzy on 2011-04-14
That message is just a warning, the update worked fine.
If you'd rather not see it again, install the medibuntu-keyring.

```
sudo apt-get --allow-unauthenticated install medibuntu-keyring
```

---

### Post by Enigmapond on 2011-04-14
You can do that or just import the key. open the terminal and do:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Cheers!

---

### Post by Rocket J Squirrel on 2011-04-14
Many thanks, guys. ):P

---

