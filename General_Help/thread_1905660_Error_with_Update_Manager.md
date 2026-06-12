---
title: "Error with Update Manager"
date: 2012-01-07
forum: General Help
---

### Post by SuperFreak on 2012-01-07
I get the following error when Update Manager comes up and I update. Any help would be appreciated ( I have 64 Bit Ubuntu 10.10):


installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 299224 files and directories currently installed.)
Preparing to replace clean-gui 3.02-0ppa31~maverick (using .../clean-gui_3.04-0ppa1~maverick_all.deb) ...
Unpacking replacement clean-gui ...
dpkg: error processing /var/cache/apt/archives/clean-gui_3.04-0ppa1~maverick_all.deb (--unpack):
 trying to overwrite '/usr/share/clean/os-uninstaller-translations.sh', which is also in package os-uninstaller 3.02-0ppa17~maverick
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/clean-gui_3.04-0ppa1~maverick_all.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

---

### Post by SuperFreak on 2012-01-08
Removed 3rd party PPA and it seems ok now

---

### Post by Rubi1200 on 2012-01-08
If the issue is resolved then please use the Thread Tools near the top of the page to mark this as Solved.

Thanks.

---

### Post by SuperFreak on 2012-01-08
Actually my problem has gotten worse. While update manager appears to be OK now I am not able to run Synaptic Manager. In the process of removing packages and a PPA,  an application I need (Logitech Media Server LMS) was removed and I can no longer reinstall it. I get an error message:
[HTML] (Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/HTML]

If anyone could now help I would be grateful. I am lost at this point.

---

### Post by yugnip on 2012-01-08
Try running the command located in the error message:

```
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
```

That should fix broken packages. Lastly you can run:

```
sudo dpkg --configure --pending
```

Hope this helps.

---

### Post by Rubi1200 on 2012-01-08
Try the commands suggested by yugnip and also the following:

```
sudo dpkg --configure -a
```

Post error messages so we can see what is going on.

Thanks.

---

### Post by SuperFreak on 2012-01-08
Repeats error message "The package logitechmediaserver needs to be reinstalled, but I can't find an archive for it." see below:

```
david@MainSqueezer:~$ sudo apt-get update
[sudo] password for david: 
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Get:1 http://dl.google.com testing Release.gpg [189B]                          
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://packages.medibuntu.org karmic Release.gpg                           
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ maverick/main Translation-en_CA
Ign http://dl.google.com/linux/deb/ testing/non-free Translation-en            
Hit http://ca.archive.ubuntu.com maverick Release.gpg                          
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://download.bitdefender.com bitdefender Release.gpg                    
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_CA       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_CA    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_CA           
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://archive.canonical.com maverick Release                              
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com/opera/ stable/non-free Translation-en                 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en  
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_CA 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_CA 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_CA   
Hit http://ca.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://archive.canonical.com maverick/partner amd64 Packages               
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://dl.google.com/linux/deb/ testing/non-free Translation-en_CA         
Hit http://archive.getdeb.net maverick-getdeb Release.gpg                      
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en      
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en_CA   
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_CA              
Hit http://deb.opera.com stable Release                                        
Ign http://packages.medibuntu.org/ karmic/free Translation-en                  
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick-backports Release.gpg                
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://deb.opera.com stable/non-free amd64 Packages                        
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Ign http://ppa.launchpad.net/unity/ppa/ubuntu/ maverick/main Translation-en    
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick Release                              
Hit http://ca.archive.ubuntu.com maverick-updates Release                      
Hit https://download.miserware.com maverick Release.gpg                        
Ign http://ppa.launchpad.net/unity/ppa/ubuntu/ maverick/main Translation-en_CA 
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ca.archive.ubuntu.com maverick-backports Release                    
Ign http://packages.medibuntu.org/ karmic/free Translation-en_CA               
Ign http://download.bitdefender.com/repos/deb/ bitdefender/non-free Translation-en
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main amd64 Packages           
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages     
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages       
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages     
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://ca.archive.ubuntu.com maverick/main Sources                         
Hit http://ca.archive.ubuntu.com maverick/restricted Sources                   
Hit http://ca.archive.ubuntu.com maverick/universe Sources                     
Hit http://ca.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://ca.archive.ubuntu.com maverick/main amd64 Packages                  
Hit http://ca.archive.ubuntu.com maverick/restricted amd64 Packages            
Hit http://ca.archive.ubuntu.com maverick/universe amd64 Packages              
Hit http://ca.archive.ubuntu.com maverick/multiverse amd64 Packages            
Hit http://ca.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://archive.getdeb.net maverick-getdeb Release                          
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ca.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://ca.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://ca.archive.ubuntu.com maverick-updates/main amd64 Packages          
Hit http://ca.archive.ubuntu.com maverick-updates/restricted amd64 Packages    
Hit http://ca.archive.ubuntu.com maverick-updates/universe amd64 Packages      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Ign http://packages.medibuntu.org/ karmic/non-free Translation-en              
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse amd64 Packages    
Hit http://ca.archive.ubuntu.com maverick-backports/main amd64 Packages        
Hit http://ca.archive.ubuntu.com maverick-backports/restricted amd64 Packages  
Hit http://ca.archive.ubuntu.com maverick-backports/universe amd64 Packages    
Hit http://ca.archive.ubuntu.com maverick-backports/multiverse amd64 Packages  
Ign https://download.miserware.com/linux/deb/ maverick/main Translation-en     
Get:2 http://dl.google.com stable Release.gpg [198B]                           
Ign http://download.bitdefender.com/repos/deb/ bitdefender/non-free Translation-en_CA
Ign http://packages.medibuntu.org/ karmic/non-free Translation-en_CA           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Hit http://archive.getdeb.net maverick-getdeb/apps amd64 Packages              
Hit http://download.bitdefender.com bitdefender Release                        
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://packages.medibuntu.org maverick Release.gpg                         
Ign https://download.miserware.com/linux/deb/ maverick/main Translation-en_CA
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_CA       
Hit https://download.miserware.com maverick Release                            
Get:3 http://dl.google.com stable Release.gpg [198B]                           
Ign http://packages.medibuntu.org/ maverick/free Translation-en_CA        
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Ign http://download.bitdefender.com bitdefender/non-free Sources               
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_CA   
Get:4 http://dl.google.com testing Release [2,513B]                            
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign https://download.miserware.com maverick/main amd64 Packages      
Get:5 http://dl.google.com stable Release [1,347B]                             
Get:6 http://dl.google.com stable Release [1,347B]                             
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_CA         
Ign https://download.miserware.com maverick/main amd64 Packages      
Hit http://packages.medibuntu.org karmic Release                     
Ign http://download.bitdefender.com bitdefender/non-free amd64 Packages        
Hit http://packages.medibuntu.org maverick Release                             
Get:7 http://dl.google.com testing/non-free amd64 Packages [786B]              
Get:8 http://dl.google.com stable/main amd64 Packages [1,192B]                 
Hit https://download.miserware.com maverick/main amd64 Packages                
Hit http://packages.medibuntu.org karmic/free amd64 Packages         
Get:9 http://dl.google.com stable/main amd64 Packages [748B]         
Hit http://packages.medibuntu.org karmic/non-free amd64 Packages       
Ign http://download.bitdefender.com bitdefender/non-free Sources
Hit http://packages.medibuntu.org maverick/free amd64 Packages
Hit http://packages.medibuntu.org maverick/non-free amd64 Packages
Ign http://download.bitdefender.com bitdefender/non-free amd64 Packages
Hit http://download.bitdefender.com bitdefender/non-free Sources
Hit http://download.bitdefender.com bitdefender/non-free amd64 Packages
Fetched 8,518B in 5s (1,456B/s)
Reading package lists... Done
david@MainSqueezer:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package logitechmediaserver needs to be reinstalled, but I can't find an archive for it.
david@MainSqueezer:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package logitechmediaserver needs to be reinstalled, but I can't find an archive for it.
david@MainSqueezer:~$ sudo dpkg --configure --pending
david@MainSqueezer:~$ sudo dpkg --configure -a
david@MainSqueezer:~$ 

```


Logitech Media Server (LMS) is marked as installed in Software Centre but does not function on my system

---

### Post by SuperFreak on 2012-01-08
Should a force remove command of Logitech Media Server (LMS) be used?

Not sure what to do so I haven't tried anything. There is a red circle with white bar across it in top panel right side that has a message indicating
 > ...logitechmediaserver needs to be reinstalled(but can't find archive for it). This usually means that your installed packages have unmet dependencies.

edit: Please forgive my impatience. I have added "deb [http://debian-origin.slimdevices.com/](http://debian-origin.slimdevices.com/) stable main" to my software sources and was finally able to open Synaptic Pkg Mngr again. I then tried to reinstall LMS but a new error appears:

> E: /var/cache/apt/archives/logitechmediaserver_7.7.1_all.deb: subprocess new post-removal script returned error exit status 1

---

### Post by SuperFreak on 2012-01-09
Yugnip, Rubi1200  I retried the commands you gave me yesterday with the following results:

```
david@MainSqueezer:~$ sudo apt-get update
[sudo] password for david: 
Get:1 http://dl.google.com testing Release.gpg [189B]
Hit http://download.bitdefender.com bitdefender Release.gpg                    
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_CA
Ign http://dl.google.com/linux/deb/ testing/non-free Translation-en            
Hit http://packages.medibuntu.org karmic Release.gpg                           
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ maverick/main Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick Release.gpg                          
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_CA       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_CA    
Ign http://debian-origin.slimdevices.com stable Release.gpg                    
Hit http://archive.canonical.com maverick Release                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_CA           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_CA
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com/opera/ stable/non-free Translation-en                 
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en  
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_CA 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_CA 
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_CA   
Hit http://ca.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://archive.getdeb.net maverick-getdeb Release.gpg                      
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en      
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en_CA   
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_CA              
Hit http://deb.opera.com stable Release                                        
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_CA
Ign http://packages.medibuntu.org/ karmic/free Translation-en                  
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://archive.canonical.com maverick/partner amd64 Packages               
Hit http://extras.ubuntu.com maverick/main Sources                             
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_CA
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://debian-origin.slimdevices.com/ stable/main Translation-en           
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick-backports Release.gpg                
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Ign http://ppa.launchpad.net/unity/ppa/ubuntu/ maverick/main Translation-en    
Ign http://ppa.launchpad.net/unity/ppa/ubuntu/ maverick/main Translation-en_CA 
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main amd64 Packages           
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages     
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages       
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages     
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick Release                              
Hit http://ca.archive.ubuntu.com maverick-updates Release                      
Hit https://download.miserware.com maverick Release.gpg                        
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://packages.medibuntu.org/ karmic/free Translation-en_CA               
Hit http://ca.archive.ubuntu.com maverick-backports Release                    
Ign http://download.bitdefender.com/repos/deb/ bitdefender/non-free Translation-en
Ign http://debian-origin.slimdevices.com/ stable/main Translation-en_CA        
Ign http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://dl.google.com/linux/deb/ testing/non-free Translation-en_CA         
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ca.archive.ubuntu.com maverick/main Sources                         
Hit http://ca.archive.ubuntu.com maverick/restricted Sources                   
Hit http://ca.archive.ubuntu.com maverick/universe Sources                     
Hit http://ca.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://ca.archive.ubuntu.com maverick/main amd64 Packages                  
Hit http://ca.archive.ubuntu.com maverick/restricted amd64 Packages            
Hit http://ca.archive.ubuntu.com maverick/universe amd64 Packages              
Hit http://ca.archive.ubuntu.com maverick/multiverse amd64 Packages            
Hit http://ca.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://archive.getdeb.net maverick-getdeb Release                          
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Get:2 http://dl.google.com stable Release.gpg [198B]                           
Ign http://packages.medibuntu.org/ karmic/non-free Translation-en              
Hit http://ca.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://ca.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://ca.archive.ubuntu.com maverick-updates/main amd64 Packages          
Hit http://ca.archive.ubuntu.com maverick-updates/restricted amd64 Packages    
Hit http://ca.archive.ubuntu.com maverick-updates/universe amd64 Packages      
Hit http://debian-origin.slimdevices.com stable Release                        
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_CA       
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse amd64 Packages    
Hit http://ca.archive.ubuntu.com maverick-backports/main amd64 Packages        
Hit http://ca.archive.ubuntu.com maverick-backports/restricted amd64 Packages  
Hit http://ca.archive.ubuntu.com maverick-backports/universe amd64 Packages    
Ign https://download.miserware.com/linux/deb/ maverick/main Translation-en     
Get:3 http://dl.google.com stable Release.gpg [198B]                           
Hit http://ca.archive.ubuntu.com maverick-backports/multiverse amd64 Packages  
Ign http://debian-origin.slimdevices.com stable/main Sources                   
Ign http://packages.medibuntu.org/ karmic/non-free Translation-en_CA           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Hit http://archive.getdeb.net maverick-getdeb/apps amd64 Packages              
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_CA   
Ign http://download.bitdefender.com/repos/deb/ bitdefender/non-free Translation-en_CA
Hit http://download.bitdefender.com bitdefender Release              
Ign http://debian-origin.slimdevices.com stable/main amd64 Packages/DiffIndex  
Hit http://packages.medibuntu.org maverick Release.gpg                         
Get:4 http://dl.google.com testing Release [2,513B]                            
Ign https://download.miserware.com/linux/deb/ maverick/main Translation-en_CA  
Get:5 http://dl.google.com stable Release [1,347B]                             
Ign http://debian-origin.slimdevices.com stable/main Sources                   
Get:6 http://dl.google.com stable Release [1,347B]                             
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Get:7 http://dl.google.com testing/non-free amd64 Packages [786B]              
Ign http://debian-origin.slimdevices.com stable/main amd64 Packages            
Ign http://packages.medibuntu.org/ maverick/free Translation-en_CA             
Hit https://download.miserware.com maverick Release                            
Err http://debian-origin.slimdevices.com stable/main Sources                   
  404  Not Found
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://download.bitdefender.com bitdefender/non-free Sources               
Ign http://debian-origin.slimdevices.com stable/main amd64 Packages            
Ign https://download.miserware.com maverick/main amd64 Packages                
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_CA         
Hit http://debian-origin.slimdevices.com stable/main amd64 Packages            
Hit http://packages.medibuntu.org karmic Release                               
Ign http://download.bitdefender.com bitdefender/non-free amd64 Packages        
Ign https://download.miserware.com maverick/main amd64 Packages                
Hit http://packages.medibuntu.org maverick Release                             
Hit http://packages.medibuntu.org karmic/free amd64 Packages                   
Ign http://download.bitdefender.com bitdefender/non-free Sources               
Hit https://download.miserware.com maverick/main amd64 Packages                
Get:8 http://dl.google.com stable/main amd64 Packages [1,192B]                 
Hit http://packages.medibuntu.org karmic/non-free amd64 Packages               
Hit http://packages.medibuntu.org maverick/free amd64 Packages                 
Ign http://download.bitdefender.com bitdefender/non-free amd64 Packages
Hit http://download.bitdefender.com bitdefender/non-free Sources               
Hit http://download.bitdefender.com bitdefender/non-free amd64 Packages        
Get:9 http://dl.google.com stable/main amd64 Packages [748B]                   
Hit http://packages.medibuntu.org maverick/non-free amd64 Packages
Fetched 8,518B in 4s (1,812B/s)
W: Failed to fetch http://debian-origin.slimdevices.com/dists/stable/main/source/Sources.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
david@MainSqueezer:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/96.9MB of archives.
After this operation, 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  logitechmediaserver
Install these packages without verification [y/N]? y
Selecting previously deselected package logitechmediaserver.
(Reading database ... 295080 files and directories currently installed.)
Preparing to replace logitechmediaserver 7.7.1 (using .../logitechmediaserver_7.7.1_all.deb) ...
Unpacking replacement logitechmediaserver ...
rm: cannot remove `/etc/apparmor.d/usr.sbin.mysqld': No such file or directory
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
rm: cannot remove `/etc/apparmor.d/usr.sbin.mysqld': No such file or directory
dpkg: error processing /var/cache/apt/archives/logitechmediaserver_7.7.1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
rm: cannot remove `/etc/apparmor.d/usr.sbin.mysqld': No such file or directory
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/logitechmediaserver_7.7.1_all.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
david@MainSqueezer:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/96.9MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  logitechmediaserver
Install these packages without verification [y/N]? y
(Reading database ... 295080 files and directories currently installed.)
Preparing to replace logitechmediaserver 7.7.1 (using .../logitechmediaserver_7.7.1_all.deb) ...
Unpacking replacement logitechmediaserver ...
rm: cannot remove `/etc/apparmor.d/usr.sbin.mysqld': No such file or directory
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
rm: cannot remove `/etc/apparmor.d/usr.sbin.mysqld': No such file or directory
dpkg: error processing /var/cache/apt/archives/logitechmediaserver_7.7.1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
rm: cannot remove `/etc/apparmor.d/usr.sbin.mysqld': No such file or directory
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/logitechmediaserver_7.7.1_all.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
david@MainSqueezer:~$ sudo dpkg --configure --pending
david@MainSqueezer:~$ sudo dpkg --configure -a
david@MainSqueezer:~$ 

```

Tried reinstalling LMS get error message see image. Very frustrating

---

### Post by SuperFreak on 2012-01-09
I seem to have fixed the problem and perhaps my success will help someone else. I had found myself in an endless loop where the original installation didn't go right, uninstall failed and the recommended reinstall came up with errors.
I found at this link:
[http://blog.bodhizazen.net/linux/apt...oken-packages/](http://blog.bodhizazen.net/linux/apt...oken-packages/) instructions
on how to remove an application with the error message
"bad inconsistent state and needs to be reinstalled."

I am back up and running again


Thanks to bodhizazen

Link seem to be broken so search at the link site under blog for "apt-get how to fix very broken packages"

---

