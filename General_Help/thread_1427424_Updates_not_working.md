---
title: "Updates not working"
date: 2010-03-11
forum: General Help
---

### Post by brunolabs on 2010-03-11
About two months ago I stopped getting new system updates.
When I go to Update Manager I get the following messages:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://pt.archive.ubuntu.com jaunty Release: Unknown error executing gpgv

W: Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/jaunty/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://pt.archive.ubuntu.com jaunty Release: Unknown error executing gpgv

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/Release.gpg  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/free/i18n/Translation-en_US.bz2  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/non-free/i18n/Translation-en_US.bz2  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/jaunty/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

How can I solve this problem?


Thanks!

---

### Post by slakkie on 2010-03-11
Looks like you are having DNS problems.

Can you do (in a terminal):

host security.ubuntu.com


if that is not working:

cat /etc/resolv.conf

---

### Post by brunolabs on 2010-03-11
> **slakkie said:**
> Looks like you are having DNS problems.

Can you do (in a terminal):

host security.ubuntu.com


I got:

security.ubuntu.com has address 91.189.88.31
security.ubuntu.com has address 91.189.88.37

---

### Post by slakkie on 2010-03-11
can you run, sudo aptitude update from the terminal as well?

---

### Post by brunolabs on 2010-03-11
> **slakkie said:**
> can you run, sudo aptitude update from the terminal as well?

Did it but got the same problem:

```
Writing extended state information... Done
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US         
Get:1 http://pt.archive.ubuntu.com jaunty Release.gpg [1964B]                                                                           
Get:2 http://security.ubuntu.com jaunty-security Release.gpg [189B]                                      
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US                                         
Ign http://pt.archive.ubuntu.com jaunty/main Translation-en_US                                                
Ign http://pt.archive.ubuntu.com jaunty/restricted Translation-en_US                                          
Ign http://pt.archive.ubuntu.com jaunty/universe Translation-en_US                                            
Ign http://pt.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://pt.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://pt.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://pt.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://pt.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://pt.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Get:3 http://security.ubuntu.com jaunty-security Release [57.9kB]    
Get:4 http://pt.archive.ubuntu.com jaunty Release [12.8kB]               
Err http://pt.archive.ubuntu.com jaunty Release                                                  
  
Hit http://packages.medibuntu.org jaunty Release.gpg                                             
Ign http://packages.medibuntu.org jaunty/free Translation-en_US           
Hit http://pt.archive.ubuntu.com jaunty-updates Release                   
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US       
Hit http://packages.medibuntu.org jaunty Release                            
Hit http://pt.archive.ubuntu.com jaunty-updates/main Packages               
Hit http://packages.medibuntu.org jaunty/free Packages
Hit http://pt.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://pt.archive.ubuntu.com jaunty-updates/main Sources
Hit http://pt.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://pt.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://pt.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://pt.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://pt.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://packages.medibuntu.org jaunty/non-free Packages
Get:5 http://security.ubuntu.com jaunty-security/main Packages [137kB]
Get:6 http://security.ubuntu.com jaunty-security/restricted Packages [2612B]
Get:7 http://security.ubuntu.com jaunty-security/main Sources [37.7kB]
Get:8 http://security.ubuntu.com jaunty-security/restricted Sources [617B]
Get:9 http://security.ubuntu.com jaunty-security/universe Packages [79.0kB]
Get:10 http://security.ubuntu.com jaunty-security/universe Sources [20.1kB]
Get:11 http://security.ubuntu.com jaunty-security/multiverse Packages [1669B]
Get:12 http://security.ubuntu.com jaunty-security/multiverse Sources [580B]
Fetched 339kB in 3s (89.4kB/s)                     
Reading package lists... Done             
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://pt.archive.ubuntu.com jaunty Release: Unknown error executing gpgv

W: **You may want to run apt-get update to correct these problems**

```

Also tried that (on bold):
```
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US         
Hit http://packages.medibuntu.org jaunty Release.gpg                                                                                    
Ign http://packages.medibuntu.org jaunty/free Translation-en_US      
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US  
Get:1 http://pt.archive.ubuntu.com jaunty Release.gpg [1964B]        
Hit http://security.ubuntu.com jaunty-security Release.gpg               
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Hit http://packages.medibuntu.org jaunty Release                     
Ign http://pt.archive.ubuntu.com jaunty/main Translation-en_US       
Ign http://pt.archive.ubuntu.com jaunty/restricted Translation-en_US 
Ign http://pt.archive.ubuntu.com jaunty/universe Translation-en_US   
Ign http://pt.archive.ubuntu.com jaunty/multiverse Translation-en_US 
Hit http://pt.archive.ubuntu.com jaunty-updates Release.gpg          
Ign http://pt.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://pt.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://pt.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://pt.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release               
Hit http://packages.medibuntu.org jaunty/free Packages
Get:2 http://pt.archive.ubuntu.com jaunty Release [12.8kB]          
Err http://pt.archive.ubuntu.com jaunty Release                                             
  
Hit http://pt.archive.ubuntu.com jaunty-updates Release                                     
Hit http://security.ubuntu.com jaunty-security/main Packages         
Hit http://packages.medibuntu.org jaunty/non-free Packages          
Hit http://pt.archive.ubuntu.com jaunty-updates/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://pt.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://pt.archive.ubuntu.com jaunty-updates/main Sources
Hit http://pt.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://pt.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://pt.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://pt.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://pt.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 1965B in 4s (418B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://pt.archive.ubuntu.com jaunty Release: Unknown error executing gpgv

W: Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/jaunty/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

How can I solve this?

---

### Post by slakkie on 2010-03-12
pt is portugal right? Could you try an alternative mirror?

eg gb.archive.ubuntu.com or nl.archive.ubuntu.com and see if that works?

Quick one-liner:

sudo perl -p -i.orig -e 's/pt.ar/nl.ar/g' /etc/apt/sources.list
This will create a backup (/etc/apt/sources.list.orig).

Then, aptitude update and see how that goes.

---

### Post by brunolabs on 2010-03-12
Worked!

Thanks for helping!

---

