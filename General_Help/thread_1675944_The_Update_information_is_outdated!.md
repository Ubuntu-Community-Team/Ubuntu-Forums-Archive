---
title: "The Update information is outdated!"
date: 2011-01-26
forum: General Help
---

### Post by meddyuk on 2011-01-26
Hiya Guys,

Wondered if anyone had a fix for this bug? I have been successfully updating my PC daily, however every now and again i get the warning triangle in the top right hand corner stating Update manger even thought updated almost daily reports "The package information was updated 26 days ago".

I have been into synaptic manager and slected best server for my updates and then i go into update manager and update the system, however, it doesnt solve it.

any ideas?

Meddy.

---

### Post by lisati on 2011-01-26
Does clicking on Update Manager's "Check" button help?

---

### Post by snowpine on 2011-01-26
Try popping open a terminal (under Applications->Accessories) and typing:

```
sudo apt-get update
```

If there are error messages, you can copy and paste them here so we can take a look for you. :)

---

### Post by ludwvin on 2011-02-11
Hello, I am having the same issue. A few weeks ago I installed Opera, and I think it is that package that is causing the warning. I ran the command above, and here is the output:

ludwvin@Laptop-ubuntu:~$ sudo apt-get update
[sudo] password for ludwvin: 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_CA           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_CA       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_CA    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_CA
Get:1 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                           
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en                 
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_CA              
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_CA 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_CA 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Get:2 [http://deb.opera.com](http://deb.opera.com) stable Release [1,063B]                             
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_CA
Err [http://deb.opera.com](http://deb.opera.com) stable Release                                        
  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security Release.gpg                 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_CA
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages     
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates Release            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security Release           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/main Sources               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/multiverse amd64 Packages
Fetched 190B in 1s (153B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by lisati on 2011-02-11
> **lisati said:**
> Does clicking on Update Manager's "Check" button help?

^^This

---

### Post by ludwvin on 2011-02-11
I've just confirmed the Opera package is causing the issue. I unchecked it from the synaptic software sources and I no longer get the warning.

---

