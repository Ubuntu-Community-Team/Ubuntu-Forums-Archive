---
title: "I cant install any programs or uninstall any programs"
date: 2012-07-11
forum: General Help
---

### Post by n123q45 on 2012-07-11
My linux will not allow me to install anything because it needs 2 b repaired. I click the repair button and its says "Package operation failed". When i click details, it says "```
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
(Reading database ... 172965 files and directories currently installed.)
Unpacking qemu-kvm (from .../qemu-kvm_1.0+noroms-0ubuntu13_i386.deb) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 kvm' returned error code 10. Exiting.
dpkg: error processing /var/cache/apt/archives/qemu-kvm_1.0+noroms-0ubuntu13_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/qemu-kvm_1.0+noroms-0ubuntu13_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of qemu:
 qemu depends on qemu-kvm; however:
  Package qemu-kvm is not installed.
dpkg: error processing qemu (--configure):
 dependency problems - leaving unconfigured
Setting up virtualbox (4.1.12-dfsg-2) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 vboxusers' returned error code 10. Exiting.
dpkg: error processing virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.1.12-dfsg-2); however:
  Package virtualbox is not configured yet.
dpkg: error processing virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
Setting up winbind (2:3.6.3-2ubuntu2.1) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 winbindd_priv' returned error code 10. Exiting.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libvirt-bin (0.9.8-2ubuntu17.1) ...
Adding group `libvirtd' (GID 126) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 libvirtd' returned error code 10. Exiting.
dpkg: error processing libvirt-bin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.1.12-dfsg-2); however:
  Package virtualbox is not configured yet.
dpkg: error processing virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtemu:
 qtemu depends on qemu; however:
  Package qemu is not configured yet.
dpkg: error processing qtemu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-winbind:
 libpam-winbind depends on winbind (= 2:3.6.3-2ubuntu2.1); however:
  Package winbind is not configured yet.
dpkg: error processing libpam-winbind (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-central ...
```". What should i do?

---

### Post by dino99 on 2012-07-11
dont know what you are trying to do, but virtualbox + qemu-kvm seems way to much complicated  :confused:

this package might be corrupted, delete it

sudo rm /var/cache/apt/archives/qemu-kvm_1.0+noroms-0ubuntu13_i386.deb


and explain clearly what is your project

---

### Post by miegiel on 2012-07-11
Hi **[COLOR="DarkOrange"]n123q45[/COLOR]**, welcome to ubuntu forums.

I don't have a solution to your problem, but do have some pointers on making posts here.

[LIST=1]
[*]Choose a title for your post that describes your problem. "Help!!!!" is to generic, most people need help of some sort here.
[*]Give as much detail as you can on what you are trying to accomplish, what you have done and what errors you get (you covered the last ;))
[*]Post terminal and other text output in a code box (see below). Use the **#** button in the post editor. It makes threads more readable (and avoids text being converted into smilies).
[/LIST]

```
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
(Reading database ... 172965 files and directories currently installed.)
Unpacking qemu-kvm (from .../qemu-kvm_1.0+noroms-0ubuntu13_i386.deb) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 kvm' returned error code 10. Exiting.
dpkg: error processing /var/cache/apt/archives/qemu-kvm_1.0+noroms-0ubuntu13_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/qemu-kvm_1.0+noroms-0ubuntu13_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of qemu:
 qemu depends on qemu-kvm; however:
  Package qemu-kvm is not installed.
dpkg: error processing qemu (--configure):
 dependency problems - leaving unconfigured
Setting up virtualbox (4.1.12-dfsg-2) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 vboxusers' returned error code 10. Exiting.
dpkg: error processing virtualbox (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.1.12-dfsg-2); however:
  Package virtualbox is not configured yet.
dpkg: error processing virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
Setting up winbind (2:3.6.3-2ubuntu2.1) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 winbindd_priv' returned error code 10. Exiting.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libvirt-bin (0.9.8-2ubuntu17.1) ...
Adding group `libvirtd' (GID 126) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 libvirtd' returned error code 10. Exiting.
dpkg: error processing libvirt-bin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.1.12-dfsg-2); however:
  Package virtualbox is not configured yet.
dpkg: error processing virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtemu:
 qtemu depends on qemu; however:
  Package qemu is not configured yet.
dpkg: error processing qtemu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-winbind:
 libpam-winbind depends on winbind (= 2:3.6.3-2ubuntu2.1); however:
  Package winbind is not configured yet.
dpkg: error processing libpam-winbind (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-central ...
```

---

### Post by n123q45 on 2012-07-11
I cant install any programs or uninstall any programs. If i open Ubuntu software center that message shows up

---

### Post by nothingspecial on 2012-07-11
Title changed to reflect the question.

---

### Post by SlugSlug on 2012-07-11
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
```
sudo apt-get update
```
```
sudo apt-get -f install
```

---

### Post by n123q45 on 2012-07-11
i took some screen shots.
[ATTACH]221074[/ATTACH]

[ATTACH]221075[/ATTACH]

[ATTACH]221076[/ATTACH]

the pics go in order from 
Screenshot from 2012-07-11 11:16:40
Screenshot from 2012-07-11 11:17:09
Screenshot from 2012-07-11 11:17:41
Screenshot from 2012-07-11 11:19:41

---

### Post by SlugSlug on 2012-07-11
post the output of my above commands 

please put them in code tags

---

### Post by n123q45 on 2012-07-11
```
nick@N123q45s:~$ sudo apt-get autoremove
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 qemu : Depends: qemu-kvm but it is not installed
E: Unmet dependencies. Try using -f.

```
```
nick@N123q45s:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
```
nick@N123q45s:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nick@N123q45s:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Ign http://extras.ubuntu.com precise InRelease                                 
Get:3 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                       
Ign http://ppa.launchpad.net precise InRelease                       
Get:4 http://us.archive.ubuntu.com precise Release [49.6 kB]         
Hit http://extras.ubuntu.com precise Release.gpg                               
Get:5 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://extras.ubuntu.com precise Release                                   
Get:7 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise Release                               
Get:8 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:9 http://us.archive.ubuntu.com precise/main Sources [934 kB]               
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:10 http://security.ubuntu.com precise-security/main Sources [23.1 kB]      
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:11 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:12 http://security.ubuntu.com precise-security/universe Sources [7,832 B]  
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:14 http://security.ubuntu.com precise-security/main i386 Packages [71.8 kB]
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [19.0 kB]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:18 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:19 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:20 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:21 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:22 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:23 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:24 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:25 http://us.archive.ubuntu.com precise-updates/main Sources [127 kB]      
Get:26 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:27 http://us.archive.ubuntu.com precise-updates/universe Sources [33.0 kB] 
Get:28 http://us.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:29 http://us.archive.ubuntu.com precise-updates/main i386 Packages [318 kB]
Get:30 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:31 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [88.6 kB]
Get:32 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:33 http://us.archive.ubuntu.com precise-backports/main Sources [1,845 B]   
Get:34 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:35 http://us.archive.ubuntu.com precise-backports/universe Sources [11.9 kB]
Get:36 http://us.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:37 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:38 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:39 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [10.2 kB]
Get:40 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 13.2 MB in 41s (321 kB/s)                                              
Reading package lists... Done

```
```
nick@N123q45s:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  qemu-kvm
The following NEW packages will be installed:
  qemu-kvm
0 upgraded, 1 newly installed, 0 to remove and 294 not upgraded.
8 not fully installed or removed.
Need to get 0 B/3,663 kB of archives.
After this operation, 10.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 172965 files and directories currently installed.)
Unpacking qemu-kvm (from .../qemu-kvm_1.0+noroms-0ubuntu13_i386.deb) ...
groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 126 kvm' returned error code 10. Exiting.
dpkg: error processing /var/cache/apt/archives/qemu-kvm_1.0+noroms-0ubuntu13_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/qemu-kvm_1.0+noroms-0ubuntu13_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SlugSlug on 2012-07-11
reboot first then 

```
sudo rm /etc/group.lock
``````
sudo rm /etc/gshadow.lock
```

then try  this again

```
sudo apt-get -f install
```

---

### Post by n123q45 on 2012-07-11
here is the result:
```
nick@N123q45s:~$ sudo rm /etc/group.lock
[sudo] password for nick: 
nick@N123q45s:~$ sudo rm /etc/gshadow.lock
nick@N123q45s:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  qemu-kvm
The following NEW packages will be installed:
  qemu-kvm
0 upgraded, 1 newly installed, 0 to remove and 294 not upgraded.
8 not fully installed or removed.
Need to get 0 B/3,663 kB of archives.
After this operation, 10.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 172965 files and directories currently installed.)
Unpacking qemu-kvm (from .../qemu-kvm_1.0+noroms-0ubuntu13_i386.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up winbind (2:3.6.3-2ubuntu2.1) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 
Setting up libpam-winbind (2:3.6.3-2ubuntu2.1) ...
Setting up libvirt-bin (0.9.8-2ubuntu17.1) ...
Adding group `libvirtd' (GID 128) ...
Done.
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/libvirt -g kvm -s /bin/false -u 115 libvirt-qemu' returned error code 1. Exiting.
dpkg: error processing libvirt-bin (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up qemu-kvm (1.0+noroms-0ubuntu13) ...
qemu-kvm start/running
Setting up qemu (1.0+noroms-0ubuntu13) ...
Setting up qtemu (2.0~alpha1-1ubuntu4) ...
Setting up virtualbox (4.1.12-dfsg-2) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Processing triggers for python-central ...
Setting up virtualbox-qt (4.1.12-dfsg-2) ...
Setting up virtualbox-dkms (4.1.12-dfsg-2) ...
Loading new virtualbox-4.1.12 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-24-generic-pae
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Errors were encountered while processing:
 libvirt-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by n123q45 on 2012-07-11
it works thx

---

### Post by SlugSlug on 2012-07-11
you also nneed to 


sudo rm /etc/passwd.lock

then 
try this again
sudo apt-get -f install

---

### Post by tumutanzi.com on 2012-07-11
> **SlugSlug said:**
> reboot first then 

```
sudo rm /etc/group.lock
``````
sudo rm /etc/gshadow.lock
```

then try  this again

```
sudo apt-get -f install
```

I once used this method, and it worked.

---

### Post by wsv on 2012-12-08
Have the same problem and it remains.:mad:

sudo apt-get autoremove:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up winbind (2:3.6.3-2ubuntu2.3) ...
 * Starting the Winbind daemon winbind                                                      [fail] 
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libpam-winbind:
 libpam-winbind depends on winbind (= 2:3.6.3-2ubuntu2.3); however:
  Package winbind is not configured yet.
dpkg: error processing libpam-winbind (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
       Errors were encountered while processing:
 winbind
 libpam-winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)
```sudo apt-get autoclean:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```sudo apt-get -f install:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up winbind (2:3.6.3-2ubuntu2.3) ...
 * Starting the Winbind daemon winbind                                                      [fail] 
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libpam-winbind:
 libpam-winbind depends on winbind (= 2:3.6.3-2ubuntu2.3); however:
  Package winbind is not configured yet.
dpkg: error processing libpam-winbind (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
       Errors were encountered while processing:
 winbind
 libpam-winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wsv on 2012-12-08
Just solved it: 
smb.conf was missing!?
renamed the backup to smb.conf;
removed samba4 and re-installed samba version 2:3.6.3-2ubuntu2.3

---

