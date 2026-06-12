---
title: "Always fails to download repository info"
date: 2010-10-12
forum: General Help
---

### Post by typos1 on 2010-10-12
I changed things in software sources back to how they were in Lucid after upgrading to Maverick and now I always get "falied to download repository information" whenever I check for updates. It says check your internet connection, but my internet connection is working fine.

---

### Post by andrewthomas on 2010-10-12
post the output of 

```
sudo apt-get update
```

from the terminal

---

### Post by typos1 on 2010-10-12
I get:

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/synce/ubuntu/](http://ppa.launchpad.net/synce/ubuntu/) maverick/main Translation-en        
Ign [http://ppa.launchpad.net/synce/ubuntu/](http://ppa.launchpad.net/synce/ubuntu/) maverick/main Translation-en_GB     
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_GB    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/rvm/smplayer/ubuntu/](http://ppa.launchpad.net/rvm/smplayer/ubuntu/) maverick/main Translation-en 
Ign [http://ppa.launchpad.net/rvm/smplayer/ubuntu/](http://ppa.launchpad.net/rvm/smplayer/ubuntu/) maverick/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB           
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB       
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Hit [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release.gpg                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_GB             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_GB
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main amd64 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted Sources 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse Sources 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main Sources     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted amd64 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse amd64 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe amd64 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free amd64 Packages       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/synce/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/synce/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by andrewthomas on 2010-10-12
[http://ppa.launchpad.net/synce/ppa/ubuntu](http://ppa.launchpad.net/synce/ppa/ubuntu) 
[http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) 

You need to remove the above ppa's from your sources.list
They do not have a maverick repo yet.

---

### Post by typos1 on 2010-10-12
Right I did think it might be something along those lines-cant I just leave them in-I may forget to re-enable them?-Thanks

By the way, waht happened to the new volume control Maverick was supposed to have?

---

### Post by andrewthomas on 2010-10-12
You can surely just comment them or disable them in software sources.  

What new icon?  It has been the same for quite a while.

---

### Post by typos1 on 2010-10-12
I wasnt talking about the icon, I was talking about the actual controls after youve clicked the icon. Was also supposed to have controls for rhythmbox as well. I saw a utube video about it:

[http://www.youtube.com/watch?v=ecj2i8kdyEU&feature=related](http://www.youtube.com/watch?v=ecj2i8kdyEU&feature=related)



But the icon has changed on my version of Maverick-its not a white box with a very faint picture in it, cant make out what it is though and certainly doenst look like anything to do with volume.

---

