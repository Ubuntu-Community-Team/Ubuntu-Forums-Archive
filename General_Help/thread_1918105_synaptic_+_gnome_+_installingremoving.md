---
title: "synaptic + gnome + installing/removing"
date: 2012-01-31
forum: General Help
---

### Post by huynhhuuhieu on 2012-01-31
[B]my prolems are mixed
1, synaptic closed immidiately after open, I have uninstall it
2, Then I installed clamav, gdm but incompletely in end
3, finaly I get terminal read [/B]
```
"huynhhuuhieu@pc:~$ sudo dpkg --configure -a
[sudo] password for huynhhuuhieu: 
Setting up gdm (3.0.4-0ubuntu11) ...
Warning: The home dir /var/lib/gdm you specified already exists.
Adding system user `gdm' (UID 172) ...
Adding new user `gdm' (UID 172) with group `gdm' ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/gdm -g gdm -s /bin/false -u 172 gdm' returned error code 1. Exiting.
dpkg: error processing gdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up clamav-base (0.97.3+dfsg-1ubuntu0.11.10.1) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 172 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.97.3+dfsg-1ubuntu0.11.10.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamtk:
 clamtk depends on clamav (>= 0.95); however:
  Package clamav is not configured yet.
 clamtk depends on clamav-freshclam (>= 0.95) | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gdm
 clamav-base
 clamav-freshclam
 clamav
 clamtk
...."
```
I don't know what happen, please help me
:KS:KS:KS

---

### Post by raja.genupula on 2012-01-31
hi man , please open your terminal 
```
sudo apt-get install -f

```
Let me know what you got . 
all the best .

---

### Post by huynhhuuhieu on 2012-01-31
```
huynhhuuhieu@pc:~$ sudo apt-get install -f
[sudo] password for huynhhuuhieu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up clamav-base (0.97.3+dfsg-1ubuntu0.11.10.1) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 172 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.97.3+dfsg-1ubuntu0.11.10.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of clamtk:
 clamtk depends on clamav (>= 0.95); however:
  Package clamav is not configured yet.
 clamtk depends on clamav-freshclam (>= 0.95) | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up gdm (3.0.4-0ubuntu11) ...
Warning: The home dir /var/lib/gdm you specified already exists.
Adding system user `gdm' (UID 172) ...
Adding new user `gdm' (UID 172) with group `gdm' ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/gdm -g gdm -s /bin/false -u 172 gdm' returned error code 1. Exiting.
dpkg: error processing gdm (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 clamtk
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
**That all I take. everything is coming worse when I try find out somethings.Now I can't install an app completely.:popcorn:**

---

### Post by raja.genupula on 2012-01-31
```
sudo rm /var/cache/apt/archives/*
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade 
```

execute them one by one . 

let me know what you got .

---

### Post by huynhhuuhieu on 2012-01-31
```
huynhhuuhieu@@macvslenin:~$ sudo **_rm /var/cache/apt/archives/*_**
[sudo] password for huynhhuuhieu: 
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
huynhhuuhieu@macvslenin:~$ sudo rm /var/cache/apt/archives/*
rm: _cannot remove `/var/cache/apt/archives/partial': Is a directory_
huynhhuuhieu@macvslenin:~$ **_sudo apt-get clean_**
huynhhuuhieu@macvslenin:~$ _**sudo apt-get update**_
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease            
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]  
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg [198 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg [198 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [40,8 kB]              
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release [40,8 kB]            
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release [40,8 kB]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex      
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources [120 kB]          
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources [1.337 B]   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources [40,8 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources [3.654 B]  
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages [280 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-vi                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-vi                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-vi                       
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2.968 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages [92,8 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6.336 B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]  
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Sources [2.207 B]      
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Sources [14 B]   
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Sources [5.882 B]  
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B]   
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages [2.819 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages [6.396 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex [72 B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex [72 B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources [26,7 kB]       
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources [14 B]    
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources [8.967 B]   
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources [1.629 B] 
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages [75,9 kB] 
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages [24,7 kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages [3.345 B]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex [73 B] 
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-vi                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-vi                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-vi                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en        
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en [55,3 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Translation-en        
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en [39,5 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en         
Fetched 925 kB in 17s (54,2 kB/s)                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
huynhhuuhieu@macvslenin:~$ **_sudo apt-get upgrade_**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  evince evince-common libevince3-3
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 2.391 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates/main evince i386 3.2.1-0ubuntu2.2 [206 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates/main libevince3-3 i386 3.2.1-0ubuntu2.2 [355 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates/main evince-common all 3.2.1-0ubuntu2.2 [1.830 kB]      
Fetched 2.391 kB in 41s (57,1 kB/s)                                                                             
(Reading database ... 236867 files and directories currently installed.)
Preparing to replace evince 3.2.1-0ubuntu2.1 (using .../evince_3.2.1-0ubuntu2.2_i386.deb) ...
Unpacking replacement evince ...
Preparing to replace libevince3-3 3.2.1-0ubuntu2.1 (using .../libevince3-3_3.2.1-0ubuntu2.2_i386.deb) ...
Unpacking replacement libevince3-3 ...
Preparing to replace evince-common 3.2.1-0ubuntu2.1 (using .../evince-common_3.2.1-0ubuntu2.2_all.deb) ...
Unpacking replacement evince-common ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Setting up clamav-base (0.97.3+dfsg-1ubuntu0.11.10.1) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 172 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.97.3+dfsg-1ubuntu0.11.10.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamtk:
 clamtk depends on clamav (>= 0.95); however:
  Package clamav is not configured yet.
 clamtk depends on clamav-freshclam (>= 0.95) | clamav-data; hoNo apport report written because the error message indicates its a followup error from a previous failure.
                                                        No apport report written because the error message indicates its a followup error from a previous failure.
                                                 No apport report written because MaxReports is reached already
                                                                                                               wever:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamtk (--configure):
 dependency problems - leaving unconfigured
Setting up gdm (3.0.4-0ubuntu11) ...
Warning: The home dir /var/lib/gdm you specified already exists.
Adding system user `gdm' (UID 172) ...
Adding new user `gdm' (UID 172) with group `gdm' ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/gdm -g gdm -s /bin/false -u 172 gdm' returned error code 1. Exiting.
dpkg: error processing gdm (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libevince3-3 (3.2.1-0ubuntu2.2) ...
No apport report written because MaxReports is reached already
                                                              Setting up evince-common (3.2.1-0ubuntu2.2) ...
Setting up evince (3.2.1-0ubuntu2.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 clamtk
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)

The situation is still not change
but thank you very much(^|^)
```

---

### Post by raja.genupula on 2012-02-01
hi man , i am sorry small correction i have forget to mention 
sudo rm -rf /var/cache/apt/archives/*

and then execute the commands i have given in the previous post . 

actually the meaning of the command is it will delete the cache of your update manager including partial files . try it . hope that helps . 

all the best and let me know what you got .

---

### Post by huynhhuuhieu on 2012-02-01
Setting up clamav-base (0.97.3+dfsg-1ubuntu0.11.10.1) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 172 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.97.3+dfsg-1ubuntu0.11.10.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 clamav-base
 clamav-freshclam
E: Sub-process /usr/bin/dpkg returned an error code (1) ???

The issue is not big now 
but I don't know what that is , i have a bit trouble. THANK FOR HELP:o

---

### Post by raja.genupula on 2012-02-01
> **huynhhuuhieu said:**
> Setting up clamav-base (0.97.3+dfsg-1ubuntu0.11.10.1) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 172 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.97.3+dfsg-1ubuntu0.11.10.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 clamav-base
 clamav-freshclam
E: Sub-process /usr/bin/dpkg returned an error code (1) ???

The issue is not big now 
but I don't know what that is , i have a bit trouble. THANK FOR HELP:o
yeah we did some progress on issue .
 
now try 

```
sudo apt-get install -f 
```

if it wont help us then do this 

```
sudo apt-get remove -f
```

let us know what you got . 

all the best,

---

### Post by huynhhuuhieu on 2012-02-01
it's the same. When I remove an bkoken package, terminal ends with "E:unable to locate package..."

---

### Post by raja.genupula on 2012-02-02
yeah now do 
```
sudo apt-get update
```
and try again with upgrade . 

I think we did it . Give me the output it can helps us to know still anything in hand . 

All the best .

---

### Post by huynhhuuhieu on 2012-02-02
I think I had a problem with user "guest". In terminal I allways get somethings like *useradd, unable to lock passwd *. Before, when logging on with guest , I haven't can use a few programs.
Could you give some suggests ?

---

### Post by raja.genupula on 2012-02-02
have you tried again ?  what you got ? is it same again ?

---

### Post by huynhhuuhieu on 2012-02-03
yes, It is. The guest account can't even be logged on

---

### Post by raja.genupula on 2012-02-03
yeah i got a solution for you . open your terminal and do this 

```
sudo rm -f /etc/gshadow.lock /etc/shadow.lock /etc/passwd.lock
```
All the best .

---

### Post by huynhhuuhieu on 2012-02-03
everything is flowing, other matter is chromium not run in "guest"
It has accurred for along times

---

### Post by raja.genupula on 2012-02-03
> **huynhhuuhieu said:**
> everything is flowing, other matter is chromium not run in "guest"
It has accurred for along times

you mean that actual was cleared ?

---

### Post by huynhhuuhieu on 2012-02-03
I'm Vietnamese, I try much and not understand what you mean.
  Commands in terminal run with no error. Thank you. I think maybe problem on chromium.

---

### Post by huynhhuuhieu on 2012-02-04
[I]huynhhuuhieu@macvslenin:~$ gksu synaptic
[PHP]
(gksu:6522): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
[/I][/PHP]

maybe it core problem
can you help me?

---

### Post by raja.genupula on 2012-02-04
yup! I got this

[http://ubuntuforums.org/showthread.php?t=1854470](http://ubuntuforums.org/showthread.php?t=1854470)

hope that helps , if anything come's up please let us know/

All the best .

---

### Post by huynhhuuhieu on 2012-02-17
I have solved it. removing a program that's why errors in synaptic, chromoum. But the 'guest' is still trouble with chomium.

---

