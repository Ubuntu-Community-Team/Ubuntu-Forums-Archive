---
title: "Sudo apt-get update, Synaptic, and Update Manager wont work."
date: 2011-09-29
forum: General Help
---

### Post by Acutical on 2011-09-29
I am on the main server. I've tried doing a clean install; I still have the same issue. 
 
```
acutical@Acutical:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources                         
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources [4,380 kB]              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,761 B]                         
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [3,198 B]                    
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [6,346 B]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources [155 kB]              
97% [1 Sources bzip2 0 B] [6 Sources 53.4 kB/155 kB 34%]          7,430 B/s 13s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages [1,550 kB]            
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]       
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages [6,021 kB]        
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex                  
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources [109 kB]           
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources [753 B]      
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources [27.7 kB]      
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Sources [1,888 B]    
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages [326 kB]     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted i386 Packages [839 B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe i386 Packages [96.2 kB]
99% [15 Packages bzip2 0 B] [17 Packages 1,042 B/96.2 kB 1%]       48.8 kB/s 1s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,264 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex          
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Sources [70.5 kB]         
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Sources [14 B]      
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Sources [11.3 kB]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Sources [657 B]     
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main i386 Packages [189 kB]    
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe i386 Packages [41.6 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse i386 Packages [2,077 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main TranslationIndex             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse TranslationIndex       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted TranslationIndex       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe TranslationIndex         
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
Fetched 10.6 MB in 3min 51s (45.6 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by garvinrick4 on 2011-09-29
Go to software sources and to tab as shown in screenshot and change mirror
to other than one you have. Button on the right side of download from choose
a different one. Just to see if it cures the problem?

---

### Post by Acutical on 2011-09-29
Not sure if it worked yet, it is reloading. I'll get back to you if it did/didn't work.

---

### Post by Acutical on 2011-09-30
No luck D:

When i was reloading, i got this error:

Failed to fetch gzip:/var/lib/apt/lists/partial/ftp.citylink.co.nz_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/ftp.citylink.co.nz_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch
Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dists/natty-updates/main/binary-i386/Packages](http://ftp.citylink.co.nz/ubuntu/dists/natty-updates/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by garvinrick4 on 2011-09-30
Try these one at a time. 
```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update

```
> Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dis...-i386/Packages]("http://ftp.citylink.co.nz/ubuntu/dists/natty-updates/main/binary-i386/Packages")  404  Not Found
Go into:
gksudo gedit /etc/apt/sources.list
And comment that line out (put a # sign in front of it and hit save.)

---

### Post by Acutical on 2011-09-30
Here is the error:

```
acutical@Acutical:~$ sudo rm /var/lib/apt/lists/* -vf 
[sudo] password for acutical: 
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-security_universe_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty_universe_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ftp.citylink.co.nz_ubuntu_dists_natty-updates_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-security_universe_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/mirror.anl.gov_pub_ubuntu_dists_natty-updates_universe_source_Sources'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_unity-2d-team_unity-2d-daily_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_unity-2d-team_unity-2d-daily_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_unity-2d-team_unity-2d-daily_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_unity-2d-team_unity-2d-daily_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources'
acutical@Acutical:~$ sudo apt-get clean all 
acutical@Acutical:~$ sudo apt-get update
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty InRelease
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates InRelease
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security InRelease
Get:1 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty Release.gpg [198 B]
Get:2 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates Release.gpg [198 B]
Get:3 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security Release.gpg [198 B]
Get:4 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty Release [39.8 kB]
Get:5 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates Release [31.4 kB]
Get:6 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security Release [31.4 kB]
Get:7 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/restricted Sources [4,104 B]
Get:8 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/main Sources [862 kB]
Get:9 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/multiverse Sources [155 kB]              
Get:10 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/universe Sources [4,380 kB]             
Get:11 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/main i386 Packages [1,550 kB]           
78% [10 Sources bzip2 0 B] [11 Packages 0 B/1,550 kB 0%]          69.0 kB/s 22s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:12 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/restricted i386 Packages [8,986 B]      
Get:13 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/universe i386 Packages [6,021 kB]       
Get:14 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/multiverse i386 Packages [183 kB]       
99% [13 Packages bzip2 0 B] [14 Packages 61.3 kB/183 kB 33%]       71.4 kB/s 1s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/main TranslationIndex                      
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/multiverse TranslationIndex                
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/restricted TranslationIndex                
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/universe TranslationIndex                  
Get:15 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/restricted Sources [753 B]      
Get:16 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/main Sources [109 kB]           
Get:17 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/multiverse Sources [1,888 B]    
Get:18 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/universe Sources [27.7 kB]      
Get:19 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/main i386 Packages [326 kB]     
Get:20 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/restricted i386 Packages [839 B]
Get:21 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/universe i386 Packages [96.2 kB]
Get:22 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/multiverse i386 Packages [4,264 B]
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/main TranslationIndex              
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/multiverse TranslationIndex        
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/restricted TranslationIndex        
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/universe TranslationIndex          
Get:23 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/restricted Sources [14 B]      
Get:24 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/main Sources [70.5 kB]         
Get:25 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/multiverse Sources [657 B]     
Get:26 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/universe Sources [11.3 kB]     
Get:27 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/main i386 Packages [189 kB]    
Get:28 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/restricted i386 Packages [14 B]
Get:29 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/universe i386 Packages [41.6 kB]
99% [27 Packages bzip2 0 B] [29 Packages 0 B/41.6 kB 0%]            106 kB/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:30 [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/multiverse i386 Packages [2,077 B]
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/main TranslationIndex             
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/multiverse TranslationIndex       
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/restricted TranslationIndex       
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/universe TranslationIndex         
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/main Translation-en_US                     
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/main Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/multiverse Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/multiverse Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/restricted Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/restricted Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/universe Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty/universe Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/main Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/main Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/multiverse Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/multiverse Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/restricted Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/restricted Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/universe Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-updates/universe Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/main Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/main Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/multiverse Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/multiverse Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/restricted Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/restricted Translation-en
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/universe Translation-en_US
Ign [http://ftp.citylink.co.nz](http://ftp.citylink.co.nz) natty-security/universe Translation-en
Fetched 14.1 MB in 4min 13s (55.7 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/ftp.citylink.co.nz_ubuntu_dists_natty_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ftp.citylink.co.nz_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ftp.citylink.co.nz_ubuntu_dists_natty-security_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
acutical@Acutical:~$
```

---

### Post by Acutical on 2011-09-30
> **garvinrick4 said:**
> Try these one at a time. 
```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update

```Go into:
gksudo gedit /etc/apt/sources.list
And comment that line out (put a # sign in front of it and hit save.)


I am in gksudo gedit /etc/apt/sources.list but i dont see Failed to fetch [http://ftp.citylink.co.nz/ubuntu/dis...-i386/Packages]("http://ftp.citylink.co.nz/ubuntu/dists/natty-updates/main/binary-i386/Packages")  404  Not Found

/I am new to ubuntu...

---

### Post by garvinrick4 on 2011-09-30
If you follow this path /var/lib/apt/lists/partial in your file system what do you
have in partial directory?

---

### Post by Acutical on 2011-09-30
Alot of failed files

---

### Post by garvinrick4 on 2011-09-30
```
sudo rm -fR /var/lib/apt/lists/*
```
```
sudo apt-get update
```

---

### Post by garvinrick4 on 2011-09-30
This just cleans things up and makes the directory "/var/lib/apt/lists/partial" and then updates. Hopefully your straitened out.

```
sudo dpkg --configure -a
```
```
sudo apt-get clean
```
```
sudo apt-get autoclean
```
```
sudo mkdir -p /var/lib/apt/lists/partial
```
```
sudo apt-get update
```

---

### Post by Acutical on 2011-09-30
Still get a error. :L

---

### Post by Acutical on 2011-09-30
> **garvinrick4 said:**
> ```
sudo rm -fR /var/lib/apt/lists/*
``````
sudo apt-get update
```

THAT WORKED!!! Thanks so much!!!

---

### Post by garvinrick4 on 2011-09-30
Hey great something had to work eventually, enjoy your Ubuntu Acutical and welcome to the Ubuntu Forums, will see you around here I am sure.

---

