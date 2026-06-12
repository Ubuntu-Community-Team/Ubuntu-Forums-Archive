---
title: "Update Question"
date: 2010-01-17
forum: General Help
---

### Post by distortedecho on 2010-01-17
Hi,

I keep getting the update notification by my clock: Red Triangle with exclamation mark. But I don't get the "available updates" icon on Docky.

If I double click the triangle, I get the "checking for updates" screen, but nothing is available - Only DeVeDe shows their is an update but it is greyed out.

What's Ubuntu trying to tell me?

---

### Post by lidex on 2010-01-17
Run these commands in a terminal and see what happens:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by distortedecho on 2010-01-18
```
desktop:~$ sudo apt-get update
Get: 1 http://security.ubuntu.com karmic-security Release.gpg [189B]
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB          
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_GB              
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                     
Hit http://gb.archive.ubuntu.com karmic Release.gpg                            
Hit http://gb.archive.ubuntu.com karmic/main Translation-en_GB                 
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB    
Get: 2 http://security.ubuntu.com karmic-security Release [44.1kB]             
Hit http://archive.canonical.com karmic Release                                
Hit http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com karmic/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB           
Get: 3 http://gb.archive.ubuntu.com karmic-updates Release.gpg [189B]          
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB   
Hit http://ppa.launchpad.net karmic Release                                    
Get: 4 http://www.bunkus.org ./ Release.gpg [189B]                             
Ign http://www.bunkus.org ./ Translation-en_GB                                 
Hit http://gb.archive.ubuntu.com karmic Release                                
Get: 5 http://gb.archive.ubuntu.com karmic-updates Release [44.1kB]            
Get: 6 http://www.bunkus.org ./ Release [1,676B]                               
Ign http://download.opensuse.org ./ Release.gpg                                
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://archive.canonical.com karmic/partner Sources                        
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://download.opensuse.org ./ Translation-en_GB                          
Ign http://www.bunkus.org ./ Release                                           
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://gb.archive.ubuntu.com karmic/main Packages                          
Hit http://gb.archive.ubuntu.com karmic/restricted Packages                    
Hit http://gb.archive.ubuntu.com karmic/main Sources                           
Hit http://gb.archive.ubuntu.com karmic/restricted Sources                     
Hit http://gb.archive.ubuntu.com karmic/universe Packages                      
Hit http://gb.archive.ubuntu.com karmic/universe Sources                       
Hit http://www.bunkus.org ./ Packages                                          
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages                    
Get: 7 http://security.ubuntu.com karmic-security/main Packages [49.2kB]       
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources                     
Get: 8 http://gb.archive.ubuntu.com karmic-updates/main Packages [142kB]       
Hit http://www.bunkus.org ./ Sources                                           
Ign http://download.opensuse.org ./ Release                                    
Ign http://download.opensuse.org ./ Packages                                   
Get: 9 http://gb.archive.ubuntu.com karmic-updates/restricted Packages [14B]   
Get: 10 http://gb.archive.ubuntu.com karmic-updates/main Sources [44.5kB]      
Get: 11 http://security.ubuntu.com karmic-security/restricted Packages [14B]   
Get: 12 http://security.ubuntu.com karmic-security/main Sources [14.0kB]       
Get: 13 http://security.ubuntu.com karmic-security/restricted Sources [14B]    
Get: 14 http://security.ubuntu.com karmic-security/universe Packages [21.1kB]  
Get: 15 http://gb.archive.ubuntu.com karmic-updates/restricted Sources [14B]   
Get: 16 http://gb.archive.ubuntu.com karmic-updates/universe Packages [87.2kB] 
Ign http://download.opensuse.org ./ Sources                                    
Get: 17 http://security.ubuntu.com karmic-security/universe Sources [3,944B]   
Get: 18 http://security.ubuntu.com karmic-security/multiverse Packages [1,666B]
Get: 19 http://security.ubuntu.com karmic-security/multiverse Sources [575B]   
Get: 20 http://gb.archive.ubuntu.com karmic-updates/universe Sources [21.2kB]  
Get: 21 http://gb.archive.ubuntu.com karmic-updates/multiverse Packages [6,942B]
Get: 22 http://gb.archive.ubuntu.com karmic-updates/multiverse Sources [3,831B]
[B][I]Ign http://download.opensuse.org ./ Packages                                
Ign http://download.opensuse.org ./ Sources       
Hit http://download.opensuse.org ./ Packages   
Err http://download.opensuse.org ./ Sources
  404  Not Found
Fetched 485kB in 1s (324kB/s)
W: GPG error: http://www.bunkus.org ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BCCF7AF0B6571FCA
W: Failed to fetch http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.04/./Sources.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.[/I][/B]
desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  devede
The following packages will be upgraded:
  cpp-4.4 g++-4.4 gcc-4.4 gcc-4.4-base libgcc1 libgomp1 libpurple-bin
  libpurple0 libstdc++6 libstdc++6-4.4-dev libthai-data libthai0 pidgin
  pidgin-data xserver-xorg-video-intel
15 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 17.8MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com karmic-updates/main libstdc++6-4.4-dev 4.4.1-4ubuntu9 [1,490kB]
Get: 2 http://gb.archive.ubuntu.com karmic-updates/main g++-4.4 4.4.1-4ubuntu9 [4,701kB]
Get: 3 http://gb.archive.ubuntu.com karmic-updates/main gcc-4.4 4.4.1-4ubuntu9 [2,976kB]
Get: 4 http://gb.archive.ubuntu.com karmic-updates/main cpp-4.4 4.4.1-4ubuntu9 [3,544kB]
Get: 5 http://gb.archive.ubuntu.com karmic-updates/main gcc-4.4-base 4.4.1-4ubuntu9 [113kB]
Get: 6 http://gb.archive.ubuntu.com karmic-updates/main libstdc++6 4.4.1-4ubuntu9 [346kB]
Get: 7 http://gb.archive.ubuntu.com karmic-updates/main libgomp1 4.4.1-4ubuntu9 [24.2kB]
Get: 8 http://gb.archive.ubuntu.com karmic-updates/main libgcc1 1:4.4.1-4ubuntu9 [55.0kB]
Get: 9 http://gb.archive.ubuntu.com karmic-updates/main libpurple-bin 1:2.6.2-1ubuntu7.1 [99.6kB]
Get: 10 http://gb.archive.ubuntu.com karmic-updates/main libpurple0 1:2.6.2-1ubuntu7.1 [1,775kB]
Get: 11 http://gb.archive.ubuntu.com karmic-updates/main libthai-data 0.1.12-1ubuntu0.2 [194kB]
Get: 12 http://gb.archive.ubuntu.com karmic-updates/main libthai0 0.1.12-1ubuntu0.2 [38.9kB]
Get: 13 http://gb.archive.ubuntu.com karmic-updates/main pidgin-data 1:2.6.2-1ubuntu7.1 [1,234kB]
Get: 14 http://gb.archive.ubuntu.com karmic-updates/main pidgin 1:2.6.2-1ubuntu7.1 [576kB]
Get: 15 http://gb.archive.ubuntu.com karmic-updates/main xserver-xorg-video-intel 2:2.9.0-1ubuntu2.1 [600kB]
Fetched 17.8MB in 32s (545kB/s)                                                
(Reading database ... 213498 files and directories currently installed.)
Preparing to replace libstdc++6-4.4-dev 4.4.1-4ubuntu8 (using .../libstdc++6-4.4-dev_4.4.1-4ubuntu9_i386.deb) ...
Unpacking replacement libstdc++6-4.4-dev ...
Preparing to replace g++-4.4 4.4.1-4ubuntu8 (using .../g++-4.4_4.4.1-4ubuntu9_i386.deb) ...
Unpacking replacement g++-4.4 ...
Preparing to replace gcc-4.4 4.4.1-4ubuntu8 (using .../gcc-4.4_4.4.1-4ubuntu9_i386.deb) ...
Unpacking replacement gcc-4.4 ...
Preparing to replace cpp-4.4 4.4.1-4ubuntu8 (using .../cpp-4.4_4.4.1-4ubuntu9_i386.deb) ...
Unpacking replacement cpp-4.4 ...
Preparing to replace gcc-4.4-base 4.4.1-4ubuntu8 (using .../gcc-4.4-base_4.4.1-4ubuntu9_i386.deb) ...
Unpacking replacement gcc-4.4-base ...
Processing triggers for man-db ...
Setting up gcc-4.4-base (4.4.1-4ubuntu9) ...
(Reading database ... 213498 files and directories currently installed.)
Preparing to replace libstdc++6 4.4.1-4ubuntu8 (using .../libstdc++6_4.4.1-4ubuntu9_i386.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.4.1-4ubuntu9) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 213498 files and directories currently installed.)
Preparing to replace libgomp1 4.4.1-4ubuntu8 (using .../libgomp1_4.4.1-4ubuntu9_i386.deb) ...
Unpacking replacement libgomp1 ...
Preparing to replace libgcc1 1:4.4.1-4ubuntu8 (using .../libgcc1_1%3a4.4.1-4ubuntu9_i386.deb) ...
Unpacking replacement libgcc1 ...
Setting up libgcc1 (1:4.4.1-4ubuntu9) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 213498 files and directories currently installed.)
Preparing to replace libpurple-bin 1:2.6.2-1ubuntu7 (using .../libpurple-bin_1%3a2.6.2-1ubuntu7.1_all.deb) ...
Unpacking replacement libpurple-bin ...
Preparing to replace libpurple0 1:2.6.2-1ubuntu7 (using .../libpurple0_1%3a2.6.2-1ubuntu7.1_i386.deb) ...
Unpacking replacement libpurple0 ...
Preparing to replace libthai-data 0.1.12-1 (using .../libthai-data_0.1.12-1ubuntu0.2_all.deb) ...
Unpacking replacement libthai-data ...
Preparing to replace libthai0 0.1.12-1 (using .../libthai0_0.1.12-1ubuntu0.2_i386.deb) ...
Unpacking replacement libthai0 ...
Preparing to replace pidgin-data 1:2.6.2-1ubuntu7 (using .../pidgin-data_1%3a2.6.2-1ubuntu7.1_all.deb) ...
Unpacking replacement pidgin-data ...
Preparing to replace pidgin 1:2.6.2-1ubuntu7 (using .../pidgin_1%3a2.6.2-1ubuntu7.1_i386.deb) ...
Unpacking replacement pidgin ...
Preparing to replace xserver-xorg-video-intel 2:2.9.0-1ubuntu2 (using .../xserver-xorg-video-intel_2%3a2.9.0-1ubuntu2.1_i386.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Setting up cpp-4.4 (4.4.1-4ubuntu9) ...
Setting up libgomp1 (4.4.1-4ubuntu9) ...

Setting up gcc-4.4 (4.4.1-4ubuntu9) ...
Setting up libpurple-bin (1:2.6.2-1ubuntu7.1) ...
Setting up libpurple0 (1:2.6.2-1ubuntu7.1) ...

Setting up libthai-data (0.1.12-1ubuntu0.2) ...
Setting up libthai0 (0.1.12-1ubuntu0.2) ...

Setting up pidgin-data (1:2.6.2-1ubuntu7.1) ...
Setting up pidgin (1:2.6.2-1ubuntu7.1) ...

Setting up xserver-xorg-video-intel (2:2.9.0-1ubuntu2.1) ...

Setting up g++-4.4 (4.4.1-4ubuntu9) ...
Setting up libstdc++6-4.4-dev (4.4.1-4ubuntu9) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
desktop:~$ 
```

---

### Post by lidex on 2010-01-18
What's your error status now?
May I ask why you have opensuse in your sources?

---

### Post by distortedecho on 2010-01-18
> **lidex said:**
> What's your error status now?
May I ask why you have opensuse in your sources?

Opensuse? I don't know, but it must have been to install... something..

The red triangle hasn't appeared today, but DeVeDe is still greyed out.

---

### Post by Uncle Spellbinder on 2010-01-18
You really need to remove OpenSUSE from your sources.list. Your problem may be from that. And even if not, it's a horrible idea (in most cases) to mix distributions.

---

### Post by 7raTEYdCql on 2010-01-18
Isn't opensuse a rpm based distribution, how can synaptic handle rpm packages. That probably is the cause of error.

If you want to convert packages from rpm to deb, don't include them in synaptic, download the rpm package and use alien to convert between the two.

---

### Post by lidex on 2010-01-18
If that doesn't do it remove the bunkus.org entries as well.

"Applications>System>Administration>Software Sources"
Third Party Software tab

---

### Post by distortedecho on 2010-01-23
Unselected opensuse and bunkus.org entries... :)

Lets see how it goes.

Thanks guys

---

