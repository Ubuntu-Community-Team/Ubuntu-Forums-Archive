---
title: "Can't Authenticate Important Packages"
date: 2010-12-22
forum: General Help
---

### Post by Jack Waugh on 2010-12-22
I'm running Lucid Lynx.  When I go into synaptic package manager and try to take updates, it says it can't authenticate some of the packages, including for example linux-image 2.6.32-27-generic.  What is up with this?

---

### Post by Verbeck on 2010-12-22
could you run *sudo apt-get update *
and post any errors here

---

### Post by Jack Waugh on 2010-12-22
```
{~/jack/adm/src} sudo apt-get update 
Get:1 http://us.archive.ubuntu.com lucid Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Get:2 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Get:3 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]            
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:4 http://dl.google.com stable Release.gpg [197B]                           
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:5 http://deb.torproject.org lucid Release.gpg [489B]             
Ign http://deb.torproject.org/torproject.org/ lucid/main Translation-en_US
Get:6 http://security.ubuntu.com lucid-security Release [38.5kB]     
Hit http://us.archive.ubuntu.com lucid Release                             
Get:7 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]              
Hit http://deb.torproject.org lucid Release                                    
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Ign http://deb.torproject.org lucid/main Packages                              
Get:8 http://dl.google.com stable Release [1,347B]                             
Ign http://deb.torproject.org lucid/main Packages                              
Get:9 http://dl.google.com stable/main Packages [1,076B]                       
Hit http://us.archive.ubuntu.com lucid/main Packages                         
Hit http://deb.torproject.org lucid/main Packages                              
Hit http://us.archive.ubuntu.com lucid/restricted Packages                   
Hit http://us.archive.ubuntu.com lucid/main Sources    
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:10 http://us.archive.ubuntu.com lucid-updates/main Packages [375kB]
Get:11 http://security.ubuntu.com lucid-security/main Packages [114kB]
Get:12 http://security.ubuntu.com lucid-security/restricted Packages [14B]     
Get:13 http://security.ubuntu.com lucid-security/main Sources [38.2kB]         
Get:14 http://security.ubuntu.com lucid-security/restricted Sources [14B]      
Get:15 http://security.ubuntu.com lucid-security/universe Packages [53.4kB]  
Get:16 http://security.ubuntu.com lucid-security/universe Sources [15.3kB]     
Get:17 http://security.ubuntu.com lucid-security/multiverse Packages [2,003B]  
Get:18 http://security.ubuntu.com lucid-security/multiverse Sources [660B]     
Get:19 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]
Get:20 http://us.archive.ubuntu.com lucid-updates/main Sources [141kB]
Get:21 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:22 http://us.archive.ubuntu.com lucid-updates/universe Packages [158kB]    
Get:23 http://us.archive.ubuntu.com lucid-updates/universe Sources [61.4kB]    
Get:24 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [7,366B] 
Get:25 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [3,677B]  
Fetched 1,061kB in 7s (137kB/s)                                                
Reading package lists... Done

```

---

### Post by Verbeck on 2010-12-22
after that, does it still say 'can't authenticate'?

---

### Post by Jack Waugh on 2010-12-22
> **Verbeck said:**
> after that, does it still say 'can't authenticate'?

No, that solved it!  Thanks!

---

