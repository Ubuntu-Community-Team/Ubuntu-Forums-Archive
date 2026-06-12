---
title: "Error on apt-get update"
date: 2011-05-01
forum: General Help
---

### Post by karthick87 on 2011-05-01
Error on apt-get update, Here are my results. How to get rid of that error?

```
karthick@Ubuntu-desktop:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN   
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN             
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN       
Get:2 http://deb.opera.com stable Release.gpg [189B]                           
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_IN              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_IN       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ailurus/ppa/ubuntu/ lucid/main Translation-en_IN  
Ign http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN
Hit http://security.ubuntu.com lucid-security Release                          
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN       
Hit http://archive.ubuntu.com lucid Release                                    
Get:3 http://deb.opera.com stable Release [1,065B]                             
Err http://deb.opera.com stable Release                                        
  
Hit http://download.virtualbox.org lucid Release.gpg                           
Ign http://ppa.launchpad.net/albyrock87/lucidoppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ lucid/main Translation-en_IN   
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/conky-companions/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://archive.ubuntu.com lucid/main Packages                              
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/non-free Translation-en_IN
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/ lucid/main Translation-en_IN
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://archive.ubuntu.com lucid/restricted Packages                        
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://archive.ubuntu.com lucid/restricted Sources               
Hit http://archive.ubuntu.com lucid/universe Packages                
Hit http://archive.ubuntu.com lucid/universe Sources                           
Hit http://archive.ubuntu.com lucid/multiverse Packages                        
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://download.virtualbox.org lucid Release                               
Ign http://ppa.launchpad.net/stefano-palazzo/stefano-testing/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/telepathy/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                       
Hit http://archive.ubuntu.com lucid/multiverse Sources                         
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release                           
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://download.virtualbox.org lucid/non-free Packages                     
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release     
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release     
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release     
Hit http://ppa.launchpad.net lucid Release                           
Ign http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Get:4 http://dl.google.com stable Release.gpg [197B]
Hit http://ppa.launchpad.net lucid/main Packages    
Hit http://ppa.launchpad.net lucid/main Sources     
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages    
Hit http://ppa.launchpad.net lucid/main Sources     
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_IN   
Get:5 http://dl.google.com stable Release [1,347B]                             
Get:6 http://dl.google.com stable Release [1,347B]                             
Get:7 http://dl.google.com stable/main Packages [1,064B]                       
Get:8 http://dl.google.com stable/main Packages [764B]                         
Fetched 5,106B in 11s (445B/s)                                                 
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  

W: Failed to fetch http://ppa.launchpad.net/albyrock87/lucidoppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Frogs Hair on 2011-05-01
I would keep trying for now , this happens to me sometimes and just keep trying until the sources connect . If it continues you may want change your sever settings in Update Manager > Settings .

---

### Post by oldos2er on 2011-05-01
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A2019EA84E7532C8
``` to get the gpg key. "404" means the file wasn't found on the server, it looks like that PPA doesn't exist anymore or has moved somewhere else.

---

### Post by karthick87 on 2011-05-01
Thank you, how to remove the unused PPA's from command line?

---

### Post by oldos2er on 2011-05-01
If the PPAs are referenced in /etc/apt/sources.list, you would run ```
sudo nano /etc/apt/sources.list
```
If it's in /etc/apt/sources.list.d/, then use ```
sudo rm ppa.list*
``` replacing "ppa" with whatever the correct name is. 
Using either process, run ```
sudo apt-get update
``` when you're done.

---

### Post by karthick87 on 2011-05-01
Thank you :)

---

