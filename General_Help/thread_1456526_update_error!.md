---
title: "update error??!??"
date: 2010-04-17
forum: General Help
---

### Post by slippycurb on 2010-04-17
:( Hello everyone and anyone. can anyone help me? seems im getting this error when i update.I searched the forums for similar errors but i found no solution that worked for me. this is the error>>>>>
****************************************************************
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead
****************************************************************

How do i get the correct key?

Yours faithfully..........Slippy

---

### Post by wojox on 2010-04-17
Copy and paste this in the terminal:

```
for i in `sudo aptitude update 2>&1 | grep NO_PUBKEY | awk '{print $NF;}'`; do sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys $i; done
```

Then:

```
sudo apt-get update
```

---

### Post by slippycurb on 2010-04-17
wow speedy response!!!!thanks:-)
no luck though. i still got the error after:-(
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IE                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_IE              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_IE                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_IE                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_IE              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                       
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IE              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_IE      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_IE            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_IE        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_IE      
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg [189B]             
Get:4 [http://dl.google.com](http://dl.google.com) stable/main Packages [925B]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_IE     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_IE 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_IE
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_IE
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release [44.1kB]               
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release                          
  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages               
Fetched 3,844B in 8s (476B/s)                                                  
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release](http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead

I thought you might to look at the long version.

---

### Post by wojox on 2010-04-17
This may help. [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by slippycurb on 2010-04-17
I tried both methods and still no joy!!!  is this something i've done?

---

### Post by slippycurb on 2010-04-17
It seems I have it fixed...sweet. use this link for more info >>>>
[http://ubuntuforums.org/showthread.php?t=1221323&highlight=badsig](http://ubuntuforums.org/showthread.php?t=1221323&highlight=badsig)

---

