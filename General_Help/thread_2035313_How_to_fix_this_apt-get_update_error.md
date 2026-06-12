---
title: "How to fix this apt-get update error?"
date: 2012-07-30
forum: General Help
---

### Post by karthick87 on 2012-07-30
How to fix this apt-get update error? (404 - Error)

```
root@chennai-justdial-cacher:~# apt-get update
Ign http://security.ubuntu.com oneiric-security InRelease                                 
Ign http://us.archive.ubuntu.com oneiric InRelease                                        
Ign http://us.archive.ubuntu.com oneiric-updates InRelease          
Ign http://us.archive.ubuntu.com oneiric-backports InRelease         
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://ppa.launchpad.net jaunty InRelease                                              
Ign http://ppa.launchpad.net oneiric InRelease                                             
Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]                      
Get:2 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                             
Get:3 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]                            
Ign http://debian.fusioninventory.org stable InRelease                                            
Ign http://ppa.launchpad.net oneiric InRelease                       
Hit http://ppa.launchpad.net oneiric Release.gpg                                           
Get:4 http://security.ubuntu.com oneiric-security Release [40.8 kB]                        
Get:5 http://debian.fusioninventory.org stable Release.gpg [198 B]                                 
Get:6 http://us.archive.ubuntu.com oneiric-backports Release.gpg [198 B]                           
Get:7 http://debian.fusioninventory.org stable Release [12.2 kB]                                            
Hit http://ppa.launchpad.net jaunty Release.gpg                                                               
Hit http://ppa.launchpad.net oneiric Release.gpg                                                               
Get:8 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                                                   
Ign http://ppa.launchpad.net oneiric Release.gpg                                                                    
Hit http://ppa.launchpad.net oneiric Release                                                                      
Hit http://ppa.launchpad.net jaunty Release                                                                                           
Get:9 http://debian.fusioninventory.org stable/main amd64 Packages [2,062 B]                                                          
Get:10 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]                                                       
Hit http://ppa.launchpad.net oneiric Release                                                                                
Get:11 http://debian.fusioninventory.org stable/main i386 Packages [2,053 B]                          
Ign http://debian.fusioninventory.org stable/main TranslationIndex                                                                                   
Get:12 http://security.ubuntu.com oneiric-security/main Sources [51.9 kB]                                                    
Get:13 http://us.archive.ubuntu.com oneiric-backports Release [40.8 kB]                                                        
Ign http://ppa.launchpad.net oneiric Release                                                                   
Hit http://ppa.launchpad.net oneiric/main Sources                                                                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                               
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                            
Hit http://ppa.launchpad.net jaunty/main Sources                                                      
Get:14 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]                                     
Hit http://ppa.launchpad.net jaunty/main amd64 Packages                                                        
Hit http://ppa.launchpad.net jaunty/main i386 Packages                                                         
Ign http://ppa.launchpad.net jaunty/main TranslationIndex                                                      
Hit http://ppa.launchpad.net oneiric/main Sources                                                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                     
Ign http://debian.fusioninventory.org stable/main Translation-en_US                                            
Get:15 http://security.ubuntu.com oneiric-security/restricted Sources [1,959 B]                     
Get:16 http://security.ubuntu.com oneiric-security/universe Sources [18.9 kB]                                              
Ign http://debian.fusioninventory.org stable/main Translation-en                                              
Get:17 http://security.ubuntu.com oneiric-security/multiverse Sources [1,641 B]                               
Get:18 http://security.ubuntu.com oneiric-security/main amd64 Packages [190 kB]                               
Err http://ppa.launchpad.net oneiric/main Sources                                                            
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                              
Ign http://ppa.launchpad.net oneiric/main Translation-en                                 
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                               
Ign http://ppa.launchpad.net jaunty/main Translation-en                                  
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                              
Ign http://ppa.launchpad.net oneiric/main Translation-en                                 
Get:19 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]                                                                                   
Get:20 http://security.ubuntu.com oneiric-security/restricted amd64 Packages [3,980 B]                                                                     
Get:21 http://security.ubuntu.com oneiric-security/universe amd64 Packages [50.6 kB]                                                                       
Get:22 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]                                                                                    
Get:23 http://security.ubuntu.com oneiric-security/multiverse amd64 Packages [3,218 B]                                                                     
Get:24 http://security.ubuntu.com oneiric-security/main i386 Packages [190 kB]                                                                             
Get:25 http://security.ubuntu.com oneiric-security/restricted i386 Packages [3,939 B]                                                                      
Get:26 http://security.ubuntu.com oneiric-security/universe i386 Packages [50.7 kB]                                                                        
Get:27 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,380 B]                                                                      
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex                                                                                      
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex                                                                                
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex                                                                                
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex                                                                                  
Hit http://security.ubuntu.com oneiric-security/main Translation-en                                                                                        
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en                                                                                  
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en                                                                                  
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                                                                                    
Get:28 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]                                                                                    
Get:29 http://us.archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]                                                                                 
Get:30 http://us.archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]                                                                            
Get:31 http://us.archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB]                                                                             
Get:32 http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]                                                                             
Get:33 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]                                                                                  
Get:34 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]                                                                             
Get:35 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]                                                                              
Get:36 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]                                                                              
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                                                                                             
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex                                                                                       
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex                                                                                       
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex                                                                                         
Get:37 http://us.archive.ubuntu.com oneiric-updates/main Sources [148 kB]                                                                                  
Get:38 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [3,347 B]                                                                           
Get:39 http://us.archive.ubuntu.com oneiric-updates/universe Sources [57.6 kB]                                                                             
Get:40 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,666 B]                                                                           
Get:41 http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages [373 kB]                                                                           
Get:42 http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [6,656 B]                                                                    
Get:43 http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages [123 kB]                                                                       
Get:44 http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,200 B]                                                                    
Get:45 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [373 kB]                                                                            
Get:46 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [6,631 B]                                                                     
Get:47 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [124 kB]                                                                        
Get:48 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,371 B]                                                                     
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex                                                                                     
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex                                                                               
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex                                                                               
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex                                                                                 
Get:49 http://us.archive.ubuntu.com oneiric-backports/main Sources [2,742 B]                                                                               
Get:50 http://us.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]                                                                            
Get:51 http://us.archive.ubuntu.com oneiric-backports/universe Sources [9,019 B]                                                                           
Get:52 http://us.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]                                                                            
Get:53 http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages [3,288 B]                                                                        
Get:54 http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages [14 B]                                                                     
Get:55 http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages [13.4 kB]                                                                    
Get:56 http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages [14 B]                                                                     
Get:57 http://us.archive.ubuntu.com oneiric-backports/main i386 Packages [3,296 B]                                                                         
Get:58 http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]                                                                      
Get:59 http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages [13.4 kB]                                                                     
Get:60 http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]                                                                      
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex                                                                                   
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex                                                                             
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex                                                                             
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex                                                                               
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                                                                                               
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en                                                                                         
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en                                                                                         
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en                                                                                           
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en                                                                                       
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                                                                 
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en                                                                                 
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en                                                                                   
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en                                                                                     
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en                                                                               
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en                                                                               
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en                                                                                 
Fetched 19.4 MB in 1min 54s (170 kB/s)                                                                                                                     
W: Failed to fetch http://ppa.launchpad.net/zentyal/2.2/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by cortman on 2012-07-30
That PPA no longer exists. Remove it from /etc/apt/sources.list, or delete its file from /etc/apt/sources.list.d.

---

### Post by oldos2er on 2012-07-30
karthick87, your sources.list is a mess. If you're running Precise, you should remove or comment out all the non-Precise repositories.

---

### Post by vasa1 on 2012-07-30
> **oldos2er said:**
> karthick87, your sources.list is a mess. If you're running Precise, you should remove or comment out all the non-Precise repositories.

I didn't want to say exactly that because I suspect he maybe using one set-up to maintain others? But otherwise, yes: 19 MB! There's 64-bit and 32-bit also.

---

### Post by karthick87 on 2012-08-01
There is no such lines found in sources.list or in sources.list.d. How do i fix?

---

### Post by plucky on 2012-08-01
> **karthick87 said:**
> There is no such lines found in sources.list or in sources.list.d. How do i fix?

Open a terminal and post the output for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```

---

### Post by karthick87 on 2012-08-01
**cat /etc/apt/sources.list**

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Alpha amd64 (20110827)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Alpha amd64 (20110827)]/ dists/oneiric/main/binary-i386/

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
# deb http://debian.fusioninventory.org/debian/ stable main
# deb-src http://debian.fusioninventory.org/debian/ stable main


#
# FusionInventory-Agent Repository
#
deb http://debian.fusioninventory.org/debian/ stable main
```

**cat /etc/apt/sources.list.d/*.list**

```
deb http://ppa.launchpad.net/fossfreedom/packagefixes/ubuntu oneiric main
deb-src http://ppa.launchpad.net/fossfreedom/packagefixes/ubuntu oneiric main
deb http://ppa.launchpad.net/ts.sch.gr/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ts.sch.gr/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/zentyal/2.2/ubuntu oneiric main

```

---

### Post by plucky on 2012-08-01
> deb-src [http://ppa.launchpad.net/zentyal/2.2/ubuntu](http://ppa.launchpad.net/zentyal/2.2/ubuntu) oneiric main

Put a # in front of that line.

The file can be found in /etc/apt/sources.list.d/

Open a terminal and ```
cd /etc/apt/sources.list.d/
ls -l
```
to find the file and delete it.

Good Luck

---

### Post by oldos2er on 2012-08-01
So you're running 11.10; it would've helped to make that clear at the beginning! :)

---

### Post by Kundan Negi on 2012-08-02
hey man,it simply means repo doesn't exist now.go to /etc/apt/sources.list or /etc/apt/sources.list.d and delete the concerned repository.

---

### Post by karthick87 on 2012-08-03
Thank you :) It fixed the problem..

---

