---
title: "Nasty Package Manager Issue"
date: 2012-07-31
forum: General Help
---

### Post by AN@S on 2012-07-31
Hello, 

I'm having few issues with Package Manager which prevents me from updating or installing new packages. I've been searching for days but non of the solutions I found have solved my issues, I know this looks like a 'traditional' problem with easy solutions, but honstly I tried everything before going on and writing this post.

Edited: Forgot to mention that I'm on Ubuntu 12.04

First of all, I'm getting an error message at the top bar, for full details on the error please check the attached snapshot.

Second, I can't start the Ubuntu Software Center, instead I get an error message that say: "System program problem detected".

Third, when I try to do an apt-get update, this is what I get:

```
Ign http://extras.ubuntu.com precise InRelease                                 
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://extras.ubuntu.com precise Release                                   
Get:2 http://dl.google.com stable InRelease                                    
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com precise/main Sources                              
Get:3 http://dl.google.com stable InRelease                                    
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:4 http://dl.google.com stable InRelease                                    
Ign http://dl.google.com stable InRelease                                      
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:5 http://dl.google.com stable/main amd64 Packages/DiffIndex                
Get:6 http://dl.google.com stable/main i386 Packages/DiffIndex                 
Get:7 http://dl.google.com stable/main TranslationIndex                        
Get:8 http://dl.google.com stable/main amd64 Packages                          
57% [8 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitingbzip2: (stdin) is not a bzip2 file.
Get:9 http://dl.google.com stable/main i386 Packages/DiffIndex                 
Get:10 http://dl.google.com stable/main TranslationIndex                       
Get:11 http://dl.google.com stable/main amd64 Packages [1,247 B]               
Get:12 http://dl.google.com stable/main i386 Packages [1,236 B]                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://ppa.launchpad.net precise InRelease                                 
Get:13 http://security.ubuntu.com precise-security Release.gpg [198 B]         
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:14 http://security.ubuntu.com precise-security Release [49.6 kB]        
Get:15 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:16 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:17 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:18 http://security.ubuntu.com precise-security/main Sources [32.4 kB]      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:19 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:20 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:21 http://ppa.launchpad.net precise/main Sources [1,823 B]                 
Get:22 http://security.ubuntu.com precise-security/universe Sources [7,849 B]  
Get:23 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:24 http://security.ubuntu.com precise-security/main amd64 Packages [118 kB]
Get:25 http://ppa.launchpad.net precise/main amd64 Packages [3,008 B]          
Get:26 http://ppa.launchpad.net precise/main i386 Packages [3,128 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:27 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:28 http://security.ubuntu.com precise-security/universe amd64 Packages [26.6 kB]
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:29 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Get:30 http://security.ubuntu.com precise-security/main i386 Packages [121 kB] 
Get:31 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:32 http://security.ubuntu.com precise-security/universe i386 Packages [26.8 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:33 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:34 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:35 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:36 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:37 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:38 http://security.ubuntu.com precise-security/main Translation-en [59.4 kB]
Get:39 http://ppa.launchpad.net precise/main Sources [24.2 kB]                 
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:40 http://ppa.launchpad.net precise/main amd64 Packages [35.3 kB]          
Get:41 http://security.ubuntu.com precise-security/universe Translation-en [17.5 kB]
Get:42 http://ppa.launchpad.net precise/main i386 Packages [35.9 kB]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://sy.archive.ubuntu.com precise InRelease                             
Ign http://sy.archive.ubuntu.com precise-updates InRelease                     
Ign http://sy.archive.ubuntu.com precise-backports InRelease                   
Get:43 http://sy.archive.ubuntu.com precise Release.gpg [198 B]
Get:44 http://sy.archive.ubuntu.com precise-updates Release.gpg [198 B]        
Get:45 http://sy.archive.ubuntu.com precise-backports Release.gpg [198 B]      
Get:46 http://sy.archive.ubuntu.com precise Release [49.6 kB]                  
Get:47 http://sy.archive.ubuntu.com precise-updates Release [49.6 kB]          
Get:48 http://sy.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:49 http://sy.archive.ubuntu.com precise/main Sources [934 kB]              
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:50 http://dl.google.com stable/main i386 Packages [1,236 B]                
Get:51 http://dl.google.com stable/main amd64 Packages                         
97% [51 Packages bzip2 0 B] [49 Sources 894 kB/934 kB 96%] [Connecting to ppa.lbzip2: (stdin) is not a bzip2 file.
Get:52 http://sy.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:53 http://sy.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:54 http://dl.google.com stable/main i386 Packages/DiffIndex                
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:55 http://dl.google.com stable/main TranslationIndex                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
96% [8 Packages xz 0 B] [53 Sources 4,783 kB/5,019 kB 95%] [Connecting to dl.go/usr/bin/xz: (stdin): File format not recognized
Get:56 http://sy.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:57 http://sy.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]     
Get:58 http://dl.google.com stable/main i386 Packages                          
89% [58 Packages bzip2 0 B] [57 Packages 393 kB/1,273 kB 31%] [Connecting to dlbzip2: (stdin) is not a bzip2 file.
93% [51 Packages xz 0 B] [57 Packages 746 kB/1,273 kB 59%] [Connecting to dl.go/usr/bin/xz: (stdin): File format not recognized
Get:59 http://dl.google.com stable/main i386 Packages                          
94% [59 Packages bzip2 0 B] [57 Packages 803 kB/1,273 kB 63%] [Connecting to dlbzip2: (stdin) is not a bzip2 file.
96% [8 Packages lzma 0 B] [57 Packages 970 kB/1,273 kB 76%] [Connecting to dl.g/usr/bin/lzma: (stdin): File format not recognized
98% [58 Packages xz 0 B] [57 Packages 1,092 kB/1,273 kB 86%] [Waiting for heade/usr/bin/xz: (stdin): File format not recognized
99% [51 Packages lzma 0 B] [57 Packages 1,163 kB/1,273 kB 91%] [Waiting for hea/usr/bin/lzma: (stdin): File format not recognized
99% [59 Packages xz 0 B] [57 Packages 1,232 kB/1,273 kB 97%] [Waiting for heade/usr/bin/xz: (stdin): File format not recognized
Get:60 http://sy.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:61 http://sy.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
64% [58 Packages lzma 0 B] [61 Packages 155 kB/4,786 kB 3%] [Waiting for header/usr/bin/lzma: (stdin): File format not recognized
67% [59 Packages lzma 0 B] [61 Packages 583 kB/4,786 kB 12%] [Waiting for heade/usr/bin/lzma: (stdin): File format not recognized
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:62 http://sy.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:63 http://sy.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:64 http://sy.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:65 http://sy.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:66 http://sy.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://sy.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://sy.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://sy.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://sy.archive.ubuntu.com precise/universe TranslationIndex             
Get:67 http://sy.archive.ubuntu.com precise-updates/main Sources [141 kB]      
Get:68 http://sy.archive.ubuntu.com precise-updates/restricted Sources [2,073 B]
Get:69 http://sy.archive.ubuntu.com precise-updates/universe Sources [43.8 kB] 
Get:70 http://sy.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:71 http://sy.archive.ubuntu.com precise-updates/main amd64 Packages [341 kB]
Get:72 http://sy.archive.ubuntu.com precise-updates/restricted amd64 Packages [3,933 B]
Get:73 http://sy.archive.ubuntu.com precise-updates/universe amd64 Packages [112 kB]
Get:74 http://sy.archive.ubuntu.com precise-updates/multiverse amd64 Packages [2,365 B]
Get:75 http://sy.archive.ubuntu.com precise-updates/main i386 Packages [344 kB]
Get:76 http://sy.archive.ubuntu.com precise-updates/restricted i386 Packages [3,949 B]
Get:77 http://sy.archive.ubuntu.com precise-updates/universe i386 Packages [113 kB]
Get:78 http://sy.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,540 B]
Get:79 http://sy.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:80 http://sy.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:81 http://sy.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:82 http://sy.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:83 http://sy.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:84 http://sy.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:85 http://sy.archive.ubuntu.com precise-backports/universe Sources [12.4 kB]
Get:86 http://sy.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:87 http://sy.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:88 http://sy.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:89 http://sy.archive.ubuntu.com precise-backports/universe amd64 Packages [11.1 kB]
Get:90 http://sy.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]
Get:91 http://sy.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:92 http://sy.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:93 http://sy.archive.ubuntu.com precise-backports/universe i386 Packages [11.2 kB]
Get:94 http://sy.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://sy.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://sy.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://sy.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://sy.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://sy.archive.ubuntu.com precise/main Translation-en                   
Hit http://sy.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://sy.archive.ubuntu.com precise/restricted Translation-en             
Hit http://sy.archive.ubuntu.com precise/universe Translation-en               
Get:95 http://sy.archive.ubuntu.com precise-updates/main Translation-en [163 kB]
Get:96 http://sy.archive.ubuntu.com precise-updates/multiverse Translation-en [1,600 B]
Get:97 http://sy.archive.ubuntu.com precise-updates/restricted Translation-en [1,083 B]
Get:98 http://sy.archive.ubuntu.com precise-updates/universe Translation-en [67.8 kB]
Hit http://sy.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://sy.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://sy.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://sy.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 20.7 MB in 4min 5s (84.2 kB/s)                                         
W: GPG error: http://dl.google.com stable InRelease: File /var/lib/apt/lists/partial/dl.google.com_linux_chrome_deb_dists_stable_InRelease doesn't start with a clearsigned message
W: GPG error: http://dl.google.com stable InRelease: File /var/lib/apt/lists/partial/dl.google.com_linux_earth_deb_dists_stable_InRelease doesn't start with a clearsigned message
W: GPG error: http://dl.google.com stable InRelease: File /var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_InRelease doesn't start with a clearsigned message
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/dl.google.com_linux_chrome_deb_dists_stable_main_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dl.google.com_linux_earth_deb_dists_stable_main_binary-amd64_Packages  Encountered a section with no Package: header

W: Failed to fetch http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/dl.google.com_linux_earth_deb_dists_stable_main_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-amd64_Packages  Encountered a section with no Package: header

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_main_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

And this is what I get when I run sudo apt-get upgrade:

```
sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```

This is my /etc/apt/sources.list file:

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://sy.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sy.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://sy.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise universe
deb http://sy.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://sy.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://sy.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://sy.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

I tried some common solutions found in this forums and other websites like:

```
# sudo dpkg --configure -a
# sudo aptitude update
# sudo aptitude upgrade
```

Also tried:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

And tried some other solutions which I can't recall now.

Thanks in advance for your help.

---

### Post by cortman on 2012-07-31
Try fixing your GPG errors by following [these instructions]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").

---

### Post by AN@S on 2012-07-31
> **cortman said:**
> Try fixing your GPG errors by following [these instructions]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").

Thank you, this allowed me to update and upgrade my system for one time only, after the update I rebooted my PC to find out that the very same error is back again! So it seems that this is not the optimal solution for my situation :(

---

### Post by AN@S on 2012-08-14
Hmmm, OK guys. Anyone else would like to help? :confused:

---

### Post by plucky on 2012-08-14
> **AN@S said:**
> Hmmm, OK guys. Anyone else would like to help? :confused:

You problems seem to stem from the Google Repositories.

Remove them and see if that fixes the problem.

Post back any errors after they have been removed from your Sources.list.

Good Luck

---

### Post by AN@S on 2012-08-14
> **plucky said:**
> You problems seem to stem from the Google Repositories.

Remove them and see if that fixes the problem.

Post back any errors after they have been removed from your Sources.list.

Good Luck

I already did that earlier, here's my current sources.list file, and I'm still getting the same error:


```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://sy.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sy.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://sy.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise universe
deb http://sy.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://sy.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://sy.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://sy.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by cortman on 2012-08-14
Check the folder /etc/apt/sources.list.d.

---

### Post by unevenflow on 2012-08-14
Hey, try this

```
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*; sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists; sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean; sudo apt-get autoclean
sudo apt-get update
sudo dpkg --clear-avail; sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get -y dist-upgrade
```

---

### Post by cortman on 2012-08-14
> **unevenflow said:**
> Hey, try this

```
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*; sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists; sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean; sudo apt-get autoclean
sudo apt-get update
sudo dpkg --clear-avail; sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get -y dist-upgrade
```

Um....

This is rather like trying to use a sledgehammer to kill a fly- read the OP's problem above and you'll understand that the solution should be much simpler.

---

### Post by AN@S on 2012-08-15
> **cortman said:**
> Check the folder /etc/apt/sources.list.d.

Thanks, the issue was with Google Repositories indeed as plucky said, I renamed sources.list.d and created a new empty one then updated without errors. It turned out that this is because Google is blocking my country from accessing some services. I renamed the sources.list.d again (so third party repositories including Google's are active again), used a VPN connection to bypass the restriction and it worked. :guitar:

Thank you guys.

---

