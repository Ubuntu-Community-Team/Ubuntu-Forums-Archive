---
title: "'dpkg was interrupted', followed by 'empty filename'"
date: 2009-08-03
forum: General Help
---

### Post by DJICS on 2009-08-03
Hi, I'm a bit new to ubuntu but have managed to survive previous problems in the updates, but this time I'm just stumped so thanks in advance to all who help me out here. There's actually lots of problems that came up so I'll try to write up everything that happened in the order it happened:

I turned my laptop on and while loading the OS, it started making a 'routine disk check' of some sort... I didn't think much of it. In this check, an error was found in root, it was fixed and the system restarted (I noticed the error message just as the countdown to restart ended so I didn't get what it was other than that). The computer turned on without any apparent problems. I proceeded to run a program (and I had run this program every day for the last week or so without any problems) and i suddenly got the following error messages:

```
/usr/include/asm-generic/errno.h:1: error: ‘d’ does not name a type
/usr/include/asm-generic/errno.h:2: error: ‘__u32’ does not name a type
/usr/include/asm-generic/errno.h:3: error: ‘__u64’ does not name a type
/usr/include/asm-generic/errno.h:4: error: ‘__u32’ does not name a type
/usr/include/asm-generic/errno.h:12: error: expected ‘;’ before ‘*’ token
/usr/include/asm-generic/errno.h:17: error: ‘nfs4_stateid’ does not name a type
/usr/include/asm-generic/errno.h:25: error: expected ‘;’ before ‘*’ token
/usr/include/asm-generic/errno.h:28: error: expected ‘;’ before ‘*’ token
/usr/include/asm-generic/errno.h:32: error: ‘nfs4_stateid’ does not name a type
```

There were many more similar messages, these are just the first few (if anyone would like to see the whole thing I'll gladly post it, just avoiding it here since its so long). Since I'm sure the program isn't the problem, I thought 'well, the disk check might have changed something, I'll go ahead and update to see if there's something else required'. However, upon updating, I got the following message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```
The previous message has been addressed in other threads. The problem would usually be that people either didn't understand they had to type in that command or that they didn't use sudo, but I did and got the following:

```
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 newline in field name `/usr/src/linux-headers-2.6.24-24-generic/include/config/ieee1394/rawio.h'
```

Once again, following what the threads said, I proceeded to remove the seemingly corrupted files from the /var/lib/dpkg/updates/ directory (namely 0000 and 0001) which allowed me to run the command without problems. However, when I proceeded to attempt an update once more, I got the following new message:

```
E: /var/cache/apt/archives/sudo_1.6.9p10-1ubuntu3.5_i386.deb: files list file for package `linux-headers-2.6.24-24' contains empty filename
```

There were some other related threads that recommended typing:

```
sudo apt-get update
```

The output for this is:

```
Err http://ubuntu.moshen.de hardy Release.gpg
  Could not resolve 'ubuntu.moshen.de'
Err http://ubuntu.moshen.de hardy/multimedia Translation-en_US                 
  Could not resolve 'ubuntu.moshen.de'
Err http://ubuntu.moshen.de hardy/misc Translation-en_US                       
  Could not resolve 'ubuntu.moshen.de'
Err http://archive.ubuntustudio.org hardy Release.gpg                          
  Could not resolve 'archive.ubuntustudio.org'
Err http://archive.ubuntustudio.org hardy/main Translation-en_US               
  Could not resolve 'archive.ubuntustudio.org'
Get:1 http://dl.google.com stable Release.gpg [191B]                           
Ign http://archive.canonical.com hardy-commercial Release.gpg                  
Ign http://archive.canonical.com hardy-commercial/main Translation-en_US       
Hit http://archive.ubuntu.com hardy Release.gpg                                
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://www.telemail.fi hardy Release.gpg                                   
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Ign http://archive.canonical.com hardy-commercial Release                      
Hit http://archive.ubuntu.com hardy-security Release.gpg                       
Hit http://archive.ubuntu.com hardy-proposed Release.gpg                       
Hit http://archive.ubuntu.com hardy Release                                    
Ign http://archive.canonical.com hardy-commercial/main Packages                
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://archive.ubuntu.com hardy-security Release                           
Hit http://archive.ubuntu.com hardy-proposed Release                           
Get:2 http://dl.google.com stable Release [1308B]                              
Err http://archive.canonical.com hardy-commercial/main Packages                
  404 Not Found
Ign http://www.telemail.fi hardy/fonts Translation-en_US                       
Hit http://archive.ubuntu.com hardy/main Sources                               
Hit http://archive.ubuntu.com hardy/restricted Sources                         
Hit http://archive.ubuntu.com hardy/universe Sources                           
Hit http://archive.ubuntu.com hardy/multiverse Sources                         
Ign http://ppa.launchpad.net hardy Release                                     
Hit http://wine.budgetdedicated.com hardy Release                              
Get:3 http://dl.google.com stable/non-free Packages [954B]                     
Hit http://repository.debuntu.org hardy Release.gpg                            
Hit http://archive.ubuntu.com hardy-updates/main Sources                       
Hit http://archive.ubuntu.com hardy-updates/restricted Sources                 
Hit http://archive.ubuntu.com hardy-updates/universe Sources                   
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources                 
Hit http://archive.ubuntu.com hardy-security/main Sources                      
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://mi.mirror.garr.it hardy-backports Release.gpg                       
Hit http://archive.ubuntu.com hardy-security/restricted Sources                
Hit http://archive.ubuntu.com hardy-security/universe Sources                  
Hit http://archive.ubuntu.com hardy-security/multiverse Sources                
Hit http://archive.ubuntu.com hardy-proposed/main Sources                      
Hit http://archive.ubuntu.com hardy-proposed/restricted Sources                
Hit http://archive.ubuntu.com hardy-proposed/universe Sources                  
Ign http://www.telemail.fi hardy/main Translation-en_US                        
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Hit ftp://ftp.osuosl.org hardy Release.gpg                                     
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://repository.debuntu.org hardy/multiverse Translation-en_US           
Hit http://archive.ubuntu.com hardy-proposed/multiverse Sources                
Ign http://hendrik.kaju.pri.ee hardy Release.gpg                               
Hit http://wine.budgetdedicated.com hardy/main Sources                         
Err http://ppa.launchpad.net hardy/main Packages                               
  404 Not Found
Hit http://wine.budgetdedicated.com hardy/main Packages                        
Ign http://mi.mirror.garr.it hardy-backports/main Translation-en_US            
Get:4 ftp://ftp.osuosl.org hardy/main Translation-en_US                        
Err http://ppa.launchpad.net hardy/main Sources                                
  404 Not Found
Ign http://www.telemail.fi hardy Release                                       
Hit http://repository.debuntu.org hardy Release                                
Ign http://mi.mirror.garr.it hardy-backports/restricted Translation-en_US      
Ign ftp://ftp.osuosl.org hardy/main Translation-en_US                          
Ign http://www.telemail.fi hardy/fonts Packages                                
Hit http://repository.debuntu.org hardy/multiverse Packages                    
Get:5 ftp://ftp.osuosl.org hardy/restricted Translation-en_US                  
Hit http://repository.debuntu.org hardy/multiverse Sources                     
Ign http://www.telemail.fi hardy/main Packages                                 
Ign ftp://ftp.osuosl.org hardy/restricted Translation-en_US                    
Ign http://www.telemail.fi hardy/fonts Sources                                 
Ign http://mi.mirror.garr.it hardy-backports/universe Translation-en_US        
Get:6 ftp://ftp.osuosl.org hardy/universe Translation-en_US                    
Ign http://mi.mirror.garr.it hardy-backports/multiverse Translation-en_US      
Ign http://www.telemail.fi hardy/main Sources                                  
Ign ftp://ftp.osuosl.org hardy/universe Translation-en_US                      
Hit http://mi.mirror.garr.it hardy-backports Release                           
Err http://www.telemail.fi hardy/fonts Packages                                
  404 Not Found
Get:7 ftp://ftp.osuosl.org hardy/multiverse Translation-en_US                  
Err http://www.telemail.fi hardy/main Packages                                 
  404 Not Found
Hit http://mi.mirror.garr.it hardy-backports/main Packages                     
Ign http://hendrik.kaju.pri.ee hardy/screenlets Translation-en_US              
Ign ftp://ftp.osuosl.org hardy/multiverse Translation-en_US                    
Err http://www.telemail.fi hardy/fonts Sources                                 
  404 Not Found
Hit ftp://ftp.osuosl.org hardy-updates Release.gpg                             
Hit http://mi.mirror.garr.it hardy-backports/restricted Packages               
Hit http://deb.opera.com etch Release.gpg                                      
Ign http://deb.opera.com etch/non-free Translation-en_US                       
Get:8 ftp://ftp.osuosl.org hardy-updates/main Translation-en_US              
Err http://www.telemail.fi hardy/main Sources                                  
  404 Not Found
Hit http://mi.mirror.garr.it hardy-backports/universe Packages                 
Hit http://deb.opera.com etch Release                                          
Ign http://deb.opera.com etch/non-free Packages                                
Hit http://mi.mirror.garr.it hardy-backports/multiverse Packages              
Ign ftp://ftp.osuosl.org hardy-updates/main Translation-en_US
Hit http://deb.opera.com etch/non-free Packages                             
Get:9 ftp://ftp.osuosl.org hardy-updates/restricted Translation-en_US       
Hit http://mi.mirror.garr.it hardy-backports/main Sources     
Hit http://mi.mirror.garr.it hardy-backports/restricted Sources                
Ign ftp://ftp.osuosl.org hardy-updates/restricted Translation-en_US            
Get:10 ftp://ftp.osuosl.org hardy-updates/universe Translation-en_US        
Ign http://hendrik.kaju.pri.ee hardy Release                                
Ign ftp://ftp.osuosl.org hardy-updates/universe Translation-en_US       
Hit http://mi.mirror.garr.it hardy-backports/universe Sources
Get:11 ftp://ftp.osuosl.org hardy-updates/multiverse Translation-en_US
Hit http://mi.mirror.garr.it hardy-backports/multiverse Sources
Ign ftp://ftp.osuosl.org hardy-updates/multiverse Translation-en_US
Hit ftp://ftp.osuosl.org hardy-security Release.gpg
Get:12 ftp://ftp.osuosl.org hardy-security/main Translation-en_US
Ign ftp://ftp.osuosl.org hardy-security/main Translation-en_US                 
Ign http://hendrik.kaju.pri.ee hardy/screenlets Packages                       
Get:13 ftp://ftp.osuosl.org hardy-security/restricted Translation-en_US        
Ign ftp://ftp.osuosl.org hardy-security/restricted Translation-en_US           
Get:14 ftp://ftp.osuosl.org hardy-security/universe Translation-en_US          
Ign ftp://ftp.osuosl.org hardy-security/universe Translation-en_US             
Get:15 ftp://ftp.osuosl.org hardy-security/multiverse Translation-en_US        
Ign ftp://ftp.osuosl.org hardy-security/multiverse Translation-en_US           
Ign http://hendrik.kaju.pri.ee hardy/screenlets Sources                        
Hit ftp://ftp.osuosl.org hardy-proposed Release.gpg                            
Get:16 ftp://ftp.osuosl.org hardy-proposed/main Translation-en_US              
Ign ftp://ftp.osuosl.org hardy-proposed/main Translation-en_US                 
Get:17 ftp://ftp.osuosl.org hardy-proposed/restricted Translation-en_US        
Ign ftp://ftp.osuosl.org hardy-proposed/restricted Translation-en_US           
Get:18 ftp://ftp.osuosl.org hardy-proposed/universe Translation-en_US          
Err http://hendrik.kaju.pri.ee hardy/screenlets Packages                       
  404 Not Found
Ign ftp://ftp.osuosl.org hardy-proposed/universe Translation-en_US             
Get:19 ftp://ftp.osuosl.org hardy-proposed/multiverse Translation-en_US        
Err http://hendrik.kaju.pri.ee hardy/screenlets Sources                        
  404 Not Found
Ign ftp://ftp.osuosl.org hardy-proposed/multiverse Translation-en_US           
Hit ftp://ftp.osuosl.org hardy Release
Hit ftp://ftp.osuosl.org hardy-updates Release
Hit ftp://ftp.osuosl.org hardy-security Release
Hit ftp://ftp.osuosl.org hardy-proposed Release
Hit ftp://ftp.osuosl.org hardy/main Packages
Hit ftp://ftp.osuosl.org hardy/restricted Packages
Hit ftp://ftp.osuosl.org hardy/universe Packages
Hit ftp://ftp.osuosl.org hardy/multiverse Packages
Hit ftp://ftp.osuosl.org hardy-updates/main Packages
Hit ftp://ftp.osuosl.org hardy-updates/restricted Packages
Hit ftp://ftp.osuosl.org hardy-updates/universe Packages
Hit ftp://ftp.osuosl.org hardy-updates/multiverse Packages
Hit ftp://ftp.osuosl.org hardy-security/main Packages
Hit ftp://ftp.osuosl.org hardy-security/restricted Packages
Hit ftp://ftp.osuosl.org hardy-security/universe Packages
Hit ftp://ftp.osuosl.org hardy-security/multiverse Packages
Hit ftp://ftp.osuosl.org hardy-proposed/main Packages
Hit ftp://ftp.osuosl.org hardy-proposed/restricted Packages
Hit ftp://ftp.osuosl.org hardy-proposed/universe Packages
Hit ftp://ftp.osuosl.org hardy-proposed/multiverse Packages
Fetched 2453B in 18s (136B/s)
Reading package lists... Done
W: Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/hardy/Release.gpg  Could not resolve 'archive.ubuntustudio.org'

W: Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntustudio.org'

W: Failed to fetch http://ubuntu.moshen.de/dists/hardy/Release.gpg  Could not resolve 'ubuntu.moshen.de'

W: Failed to fetch http://ubuntu.moshen.de/dists/hardy/multimedia/i18n/Translation-en_US.bz2  Could not resolve 'ubuntu.moshen.de'

W: Failed to fetch http://ubuntu.moshen.de/dists/hardy/misc/i18n/Translation-en_US.bz2  Could not resolve 'ubuntu.moshen.de'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy-commercial/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/amaranth/ubuntu/dists/hardy/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/amaranth/ubuntu/dists/hardy/main/source/Sources.gz  404 Not Found

W: Failed to fetch http://www.telemail.fi/mlind/ubuntu/dists/hardy/fonts/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://www.telemail.fi/mlind/ubuntu/dists/hardy/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://www.telemail.fi/mlind/ubuntu/dists/hardy/fonts/source/Sources.gz  404 Not Found

W: Failed to fetch http://www.telemail.fi/mlind/ubuntu/dists/hardy/main/source/Sources.gz  404 Not Found

W: Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/hardy/screenlets/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://hendrik.kaju.pri.ee/ubuntu/dists/hardy/screenlets/source/Sources.gz  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

If you need any more info, just ask for it. Thanks again.

---

### Post by wojox on 2009-08-03
Are you runing Hardy?

Run:
```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
You may also need to go to System > Admin > Update Manager and update your source file.

---

### Post by DJICS on 2009-08-03
Hi. Yes this is Hardy. I ran the 'clean' command followed by the 'update' command and it seems that 'clean' had no effect since I got the same result I was previously getting from the 'update' command. I went ahead and tried the 'upgrade' command to see if made any difference and I got the following (I guess the last few lines are the important ones... too many errors):

```
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  bind9-host dnsutils libbind9-30 libdns35 libisc35 libisccc30 libisccfg30
  liblwres30 libnspr4-0d libnss3-1d sudo
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2282kB of archives.
After this operation, 8192B disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 ftp://ftp.osuosl.org hardy-proposed/main sudo 1.6.9p10-1ubuntu3.5 [176kB]
Get:2 ftp://ftp.osuosl.org hardy-updates/main bind9-host 1:9.4.2.dfsg.P2-2ubuntu0.2 [57.0kB]
Get:3 ftp://ftp.osuosl.org hardy-updates/main dnsutils 1:9.4.2.dfsg.P2-2ubuntu0.2 [135kB]
Get:4 ftp://ftp.osuosl.org hardy-updates/main libdns35 1:9.4.2.dfsg.P2-2ubuntu0.2 [494kB]
Get:5 ftp://ftp.osuosl.org hardy-updates/main libisc35 1:9.4.2.dfsg.P2-2ubuntu0.2 [127kB]
Get:6 ftp://ftp.osuosl.org hardy-updates/main libisccc30 1:9.4.2.dfsg.P2-2ubuntu0.2 [23.4kB]
Get:7 ftp://ftp.osuosl.org hardy-updates/main libisccfg30 1:9.4.2.dfsg.P2-2ubuntu0.2 [38.7kB]
Get:8 ftp://ftp.osuosl.org hardy-updates/main liblwres30 1:9.4.2.dfsg.P2-2ubuntu0.2 [40.6kB]
Get:9 ftp://ftp.osuosl.org hardy-updates/main libbind9-30 1:9.4.2.dfsg.P2-2ubuntu0.2 [27.8kB]
Get:10 ftp://ftp.osuosl.org hardy-proposed/main libnspr4-0d 4.7.5-0ubuntu0.8.04.1 [122kB]
Get:11 ftp://ftp.osuosl.org hardy-proposed/main libnss3-1d 3.12.3.1-0ubuntu0.8.04.1 [1040kB]
Fetched 2282kB in 9s (236kB/s)                                                 
(Reading database ... dpkg: error processing /var/cache/apt/archives/sudo_1.6.9p10-1ubuntu3.5_i386.deb (--unpack):
 files list file for package `linux-headers-2.6.24-24' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/sudo_1.6.9p10-1ubuntu3.5_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

As for the update to the source file, are you referring to anything in particular? The update window doesn't have many options I guess... I just did a Check and an Install Updates and I get the error I previously mentioned:
```

E: /var/cache/apt/archives/sudo_1.6.9p10-1ubuntu3.5_i386.deb: files list file for package `linux-headers-2.6.24-24' contains empty filename
```

---

### Post by DJICS on 2009-08-04
Also thought I should point out I have a 64-bit system. Not sure if it affects anything though...

---

