---
title: "Unable to update package list in natty"
date: 2011-05-05
forum: General Help
---

### Post by devj1988 on 2011-05-05
Hi,

 I have been trying to apt-get update and it fails :

 sudo apt-get update -o Acquire::http::No-Cache=True

Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                         
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,078 B]                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg                       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main amd64 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted amd64 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe amd64 Packages [72.5 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex [23.0 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [8,815 B]                    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse amd64 Packages [21.8 kB]      
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages [14.7 kB]             
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex [14 B]             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted amd64 Packages [18.4 kB]
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en [9,301 B]            
82% [11 Translation-en bzip2 0 B] [10 Packages 12.0 kB/18.4 kB 65%] [Waiting fobzip2: (stdin) is not a bzip2 file.
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US [15.5 kB]         
87% [12 Translation-en_US bzip2 0 B] [Waiting for headers] [Waiting for headersbzip2: (stdin) is not a bzip2 file.
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe amd64 Packages [14 B]  
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse amd64 Packages [5,491 B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex [14 B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex          
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US [30.0 kB]         
89% [16 Translation-en_US xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
89% [11 Translation-en xz 0 B] [Waiting for headers]               12.7 kB/s 1s/usr/bin/xz: (stdin): File format not recognized
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main TranslationIndex             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse TranslationIndex       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted TranslationIndex       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe TranslationIndex         
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en [92.3 kB]           
92% [17 Translation-en bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en [20.1 kB]   
81% [18 Translation-en bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_US [20 B]
81% [19 Translation-en_US bzip2 0 B] [Waiting for headers] [Waiting for headersbzip2: (stdin) is not a bzip2 file.
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en [5,145 B]
81% [20 Translation-en bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US [20 B]
81% [21 Translation-en_US bzip2 0 B] [Waiting for headers] [Waiting for headersbzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main amd64 Packages                
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main amd64 Packages               
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted amd64 Packages
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe amd64 Packages
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse amd64 Packages
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Translation-en               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Translation-en
Fetched 340 kB in 1min 54s (2,962 B/s)
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_natty_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.




my sources list :
cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

other info:

i am using a 64-bit machine. i have juggled between the us server, main server, and a few other servers also....still it fails.

i tried deleting everything in /var/cache/apt/archives/   ....was of no use.

Can anyone help me please ?


Regards,
Dev

---

### Post by plucky on 2011-05-05
> W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_bin ary-amd64_Packages Hash Sum mismatch


Have a look in that directory as there shouldn't be any files in there.

Post output of ```
ls -l /var/lib/apt/lists/partial/
```

Also try disabling all the PPAs in Software Sources.

Delete all the list files with ```
sudo rm /var/lib/apt/lists/*
```

Then reload with ```
sudo apt-get update
```

---

### Post by ThisisRuge on 2011-05-08
I'm also having the "hash sum mismatch" error everytime I download a package. Its extremely frustrating because I am on wireless broadband and each time i download 80% of a driver package and it fails, its wasted bandwidth (and a very limited resource on wireless BB).

If anyone knows the issues with "hash sum mismatch" and its fixes it would be greatly appreciated :)

These ongoing issues are causing me to burn bandwidth and sadly it could make my first Ubuntu experience a short lived one :(

---

### Post by devj1988 on 2011-05-09
@plucky:

This time i did what you told me. still doesnt work.

I changed the mirror to [http://ftp.sunet.se](http://ftp.sunet.se)

Result of: ls -l /var/lib/apt/lists/partial/



total 7576
-rw-r--r-- 1 root root      20 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_main_i18n_Translation-en
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_main_i18n_Translation-en.decomp
-rw-r--r-- 1 root root    5304 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_multiverse_binary-amd64_Packages
-rw-r--r-- 1 root root   15433 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_multiverse_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root      20 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_multiverse_i18n_Translation-en
-rw-r--r-- 1 root root    5378 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_multiverse_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_multiverse_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_multiverse_i18n_Translation-en.decomp
-rw-r--r-- 1 root root   19524 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_restricted_binary-amd64_Packages
-rw-r--r-- 1 root root   69858 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_restricted_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root   93789 2011-05-08 15:46 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_restricted_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_restricted_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root      14 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-security_main_source_Sources
-rw-r--r-- 1 root root       0 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-security_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root 5430266 2011-04-26 17:46 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-security_restricted_binary-amd64_Packages
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-security_restricted_binary-amd64_Packages.decomp
-rw-r--r-- 1 root root 1986777 2011-04-26 17:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-security_universe_binary-amd64_Packages
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-security_universe_binary-amd64_Packages.decomp
-rw-r--r-- 1 root root      14 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_universe_binary-amd64_Packages
-rw-r--r-- 1 root root       0 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty_universe_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root      20 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_main_i18n_Translation-en
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_main_i18n_Translation-en.decomp
-rw-r--r-- 1 root root      14 2011-05-08 15:46 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_main_source_Sources
-rw-r--r-- 1 root root       0 2011-05-08 15:46 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    2151 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages
-rw-r--r-- 1 root root    5257 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root      20 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en
-rw-r--r-- 1 root root    1980 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en.decomp
-rw-r--r-- 1 root root    4939 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages
-rw-r--r-- 1 root root   13555 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root      20 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_restricted_i18n_Translation-en
-rw-r--r-- 1 root root   17718 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_restricted_i18n_Translation-en.decomp
-rw-r--r-- 1 root root      14 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_universe_binary-amd64_Packages
-rw-r--r-- 1 root root       0 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_universe_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root      20 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_universe_i18n_Translation-en
-rw-r--r-- 1 root root    9301 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_universe_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_universe_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root       0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubuntu_dists_natty-updates_universe_i18n_Translation-en.decomp

---

### Post by plucky on 2011-05-09
Result of: ls -l /var/lib/apt/lists/partial/



```
total 7576
-rw-r--r-- 1 root root 20 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_main_i18n_Translation-en
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_main_i18n_Translation-en.decomp
-rw-r--r-- 1 root root 5304 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_multiverse_binary-amd64_Packages
-rw-r--r-- 1 root root 15433 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_multiverse_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root 20 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_multiverse_i18n_Translation-en
-rw-r--r-- 1 root root 5378 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_multiverse_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_multiverse_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_multiverse_i18n_Translation-en.decomp
-rw-r--r-- 1 root root 19524 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_restricted_binary-amd64_Packages
-rw-r--r-- 1 root root 69858 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_restricted_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root 93789 2011-05-08 15:46 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_restricted_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_restricted_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root 14 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-security_main_source_Sources
-rw-r--r-- 1 root root 0 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-security_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root 5430266 2011-04-26 17:46 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-security_restricted_binary-amd64_Packages
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-security_restricted_binary-amd64_Packages.decomp
-rw-r--r-- 1 root root 1986777 2011-04-26 17:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-security_universe_binary-amd64_Packages
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-security_universe_binary-amd64_Packages.decomp
-rw-r--r-- 1 root root 14 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_universe_binary-amd64_Packages
-rw-r--r-- 1 root root 0 2011-05-08 15:57 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty_universe_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root 20 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_main_i18n_Translation-en
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_main_i18n_Translation-en.decomp
-rw-r--r-- 1 root root 14 2011-05-08 15:46 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_main_source_Sources
-rw-r--r-- 1 root root 0 2011-05-08 15:46 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root 2151 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_multiverse_binary-amd64_Packages
-rw-r--r-- 1 root root 5257 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_multiverse_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root 20 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_multiverse_i18n_Translation-en
-rw-r--r-- 1 root root 1980 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_multiverse_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_multiverse_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_multiverse_i18n_Translation-en.decomp
-rw-r--r-- 1 root root 4939 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_restricted_binary-amd64_Packages
-rw-r--r-- 1 root root 13555 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_restricted_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root 20 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_restricted_i18n_Translation-en
-rw-r--r-- 1 root root 17718 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_restricted_i18n_Translation-en.decomp
-rw-r--r-- 1 root root 14 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_universe_binary-amd64_Packages
-rw-r--r-- 1 root root 0 2011-05-08 15:37 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_universe_binary-amd64_Packages.decomp.FAILED
-rw-r--r-- 1 root root 20 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_universe_i18n_Translation-en
-rw-r--r-- 1 root root 9301 2011-05-08 15:35 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_universe_i18n_Translation-en%5fUS
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_universe_i18n_Translation-en%5fUS.decomp
-rw-r--r-- 1 root root 0 2011-05-09 15:13 ftp.sunet.se_pub_os_Linux_distributions_ubuntu_ubu ntu_dists_natty-updates_universe_i18n_Translation-en.decomp 
```

That directory needs to be empty,so delete all the files in there.

```
sudo rm /var/lib/apt/lists/partial/
```

Then run ```
sudo apt-get update
``` and post the result.

---

### Post by joe carolan on 2011-05-09
same problem solved by going to synaptic and check "edit" select " repositories"
make sure no duplicates remove any you find

---

### Post by joe carolan on 2011-05-09
Sorry update previous post check "settings in synaptic then repositories"

---

### Post by joe carolan on 2011-05-09
Also noticed in synaptic package manager a whole lot of disabled software sources in other software option these were disabled in the natty upgrade process.
If you re enable some of these, this also causes the update problem.

---

### Post by stevopedia on 2011-05-17
I have the same issue. I have no third party PPAs selected.

stephen@zephyr:~$ sudo apt-get update
[sudo] password for stephen: 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed InRelease            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release              
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main amd64 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe amd64 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe TranslationIndex      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en
Reading package lists... Done

Sources: (cat /etc/apt/sources.list)
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

/var/lib/apt/lists/partial is empty. I have no idea what's going on. I know it's not a network issue.

---

### Post by venik212 on 2011-06-09
I had exactly the same problem, which is pathetic, given that these kind of problems date back to 2007 or before.  The system should be able to fix them automatically-- I spent a LOT of time trying to figure this out, and the solution could have been automated (or at least-- some meaningful error message could have been generated).
In any event, I have finally found the culprits as two repositories (sun-java and Googletalk), unchecked them in the repository list, and now everything is fine (except that I shall not be able to update Chromium browser and Java-- a small price to pay for the privilege of using open source software, I guess).

---

