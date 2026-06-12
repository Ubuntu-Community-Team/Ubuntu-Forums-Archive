---
title: "what cases this error"
date: 2011-10-24
forum: General Help
---

### Post by Elshentenawy on 2011-10-24
Greeting 
I got this error when I'm tring to download several progarms *samba* ?

failed to download package files 
check your internet connection >>>my internet connection work fine?
ok>>

Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.
Details   
libuser1 python-libuser samba system-config-samba

and when I tried to install it using terminal 

WARNING: The following packages cannot be authenticated!
  samba
Install these packages without verification [y/N]? 
 Yes ....
dpkg: warning: 'find' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)  
ThanQ

---

### Post by CerberusCommand on 2011-10-24
It may mean that samba is incompatible with 11.10 since it doesn't have a bug maintainer (Supervisor) yet according to Launchpad and it was last updated on 2011-09-30 before Oneiric Ocelot was released.

---

### Post by 2F4U on 2011-10-24
What download mirror are you using? It may be caused by a not fully synched mirror. Try switching to the main repository mirror.

---

### Post by Elshentenawy on 2011-10-24
i don't know what mirror I follow an youtube video instructions and it works fine on ubuntu 11.10 ..

---

### Post by searchfgold6789 on 2011-10-24
In a terminal, can you run ```
sudo apt-get update
``` and try again? If it fails, can you post the output?
 - search

---

### Post by Elshentenawy on 2011-10-24
here is the out put from sudo apt-get update 
I tried to install samba again and I got the same error ?
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease            
Get:1 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]       
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                                             
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources/DiffIndex                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources/DiffIndex   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease         
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources/DiffIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources             
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources/DiffIndex                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages/DiffIndex                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages       
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages/DiffIndex                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages/DiffIndex                                           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages/DiffIndex                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                                                                
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: NODATA 2

---

### Post by searchfgold6789 on 2011-10-24
You can try the commands I found at [this]("http://ubuntuforums.org/showthread.php?t=1867630") thread:```
sudo su
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

### Post by Elshentenawy on 2011-10-24
The update downloaded successfully
190 updates have been selected .The updates have been downloaded but not installed 
 but when I press install updates .. 


Package operation failed
The installation or removal of a software package failed.

installArchives() failed: 
Extracting templates from packages: 15%%
Extracting templates from packages: 31%%
Extracting templates from packages: 47%%
Extracting templates from packages: 63%%
Extracting templates from packages: 78%%
Extracting templates from packages: 94%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 15%%
Extracting templates from packages: 31%%
Extracting templates from packages: 47%%
Extracting templates from packages: 63%%
Extracting templates from packages: 78%%
Extracting templates from packages: 94%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 15%%
Extracting templates from packages: 31%%
Extracting templates from packages: 47%%
Extracting templates from packages: 63%%
Extracting templates from packages: 78%%
Extracting templates from packages: 94%%
Extracting templates from packages: 100%%
Preconfiguring packages ...
dpkg: warning: 'find' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

---

### Post by searchfgold6789 on 2011-10-24
try:```
sudo dpkg --configure -a
```Are you running the updates from the terminal?
 - search

---

### Post by Elshentenawy on 2011-10-24
yes i did 

ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: warning: 'find' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

---

### Post by Elshentenawy on 2011-10-24
I cannt update I cannt install soft wares what should I do ?

---

