---
title: "Cannot install programs via Muon Software Center"
date: 2012-08-01
forum: General Help
---

### Post by IAmNoOne on 2012-08-01
Hi, I hope this is the right place to post about my problem, otherwise please move it appropriately. Also, please bear with me as this is one bear of a problem I am having, as I also have trouble with installing packages via the Terminal.

I recently installed Kubuntu 12.04 64-bit on my pc and so far everything is working fine, except that I cannot install programs via Muon Software Center.  I keep getting the following errors:

> Changes could not be applied since some packages could not be downloaded.

or it complains about some other package manager running, which I am able to resolve, but I keep getting the above error afterwards.  This happens on any random program I install from the above mentioned package manager.

I've talked with a friend of mine who suggested a few commands I could try to resolve this problem, but I am experiencing problems with them as well.

```
sudo apt-get clean
```I ran that, but nothing happened. Okay, whatever. So then I type the next command (bear with me, this is going to be long):

```

sudo apt-get update && sudo apt-get upgrade

(Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease                               
Ign http://archive.canonical.com precise InRelease                                        
Ign http://ppa.launchpad.net precise InRelease                                            
Ign http://ppa.launchpad.net precise InRelease                                            
Ign http://security.ubuntu.com precise-security InRelease                                 
Ign http://extras.ubuntu.com precise InRelease                                            
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]                            
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                     
Get:3 http://archive.canonical.com precise Release.gpg [198 B]                            
Hit http://ppa.launchpad.net precise Release.gpg                                          
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]                     
Get:5 http://extras.ubuntu.com precise Release.gpg [72 B]                                 
Get:6 http://us.archive.ubuntu.com precise Release [49.6 kB]                               
Get:7 http://archive.canonical.com precise Release [7,078 B]                               
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]                        
Hit http://ppa.launchpad.net precise Release.gpg                                           
Hit http://extras.ubuntu.com precise Release                                               
Hit http://ppa.launchpad.net precise Release                                               
Get:9 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                       
Get:10 http://archive.canonical.com precise/partner Sources [3,428 B]                      
Hit http://ppa.launchpad.net precise Release                                               
Hit http://extras.ubuntu.com precise/main Sources                                          
Get:11 http://archive.canonical.com precise/partner amd64 Packages [4,354 B]               
Get:12 http://archive.canonical.com precise/partner i386 Packages [5,043 B]                
Ign http://archive.canonical.com precise/partner TranslationIndex                          
Hit http://ppa.launchpad.net precise/main Sources                                          
Hit http://ppa.launchpad.net precise/main amd64 Packages                                   
Hit http://ppa.launchpad.net precise/main i386 Packages                                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                                 
Get:13 http://security.ubuntu.com precise-security/restricted Sources [14 B]               
Hit http://extras.ubuntu.com precise/main amd64 Packages                                   
Hit http://extras.ubuntu.com precise/main i386 Packages                                    
Hit http://ppa.launchpad.net precise/main Sources                                          
Hit http://ppa.launchpad.net precise/main amd64 Packages                                   
Hit http://ppa.launchpad.net precise/main i386 Packages                                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                                 
Get:14 http://security.ubuntu.com precise-security/main Sources [32.4 kB]                  
Ign http://extras.ubuntu.com precise/main TranslationIndex                                 
Get:15 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]                   
Get:16 http://us.archive.ubuntu.com precise/main Sources [934 kB]                          
Get:17 http://security.ubuntu.com precise-security/multiverse Sources [713 B]              
Get:18 http://security.ubuntu.com precise-security/universe Sources [7,849 B]              
Get:19 http://security.ubuntu.com precise-security/main amd64 Packages [118 kB]            
Get:20 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]        
Get:21 http://security.ubuntu.com precise-security/universe amd64 Packages [26.6 kB]       
Get:22 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]     
Get:23 http://security.ubuntu.com precise-security/main i386 Packages [121 kB]             
Ign http://archive.canonical.com precise/partner Translation-en_US                         
Ign http://archive.canonical.com precise/partner Translation-en                            
Ign http://extras.ubuntu.com precise/main Translation-en_US                                
Get:24 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]      
Get:25 http://security.ubuntu.com precise-security/universe i386 Packages [26.8 kB]
Get:26 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]      
Ign http://extras.ubuntu.com precise/main Translation-en                                   
Get:27 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]            
Get:28 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]  
Get:29 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]  
Get:30 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]    
Get:31 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]                    
Ign http://ppa.launchpad.net precise/main Translation-en_US                                
Get:32 http://security.ubuntu.com precise-security/main Translation-en [59.4 kB]           
Ign http://ppa.launchpad.net precise/main Translation-en                                   
Ign http://ppa.launchpad.net precise/main Translation-en_US                                
Get:33 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]                    
Ign http://ppa.launchpad.net precise/main Translation-en                                   
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                  
Hit http://security.ubuntu.com precise-security/restricted Translation-en 
Get:34 http://security.ubuntu.com precise-security/universe Translation-en [17.5 kB]
Get:35 http://us.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]                 
Get:36 http://us.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]            
Get:37 http://us.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]             
Get:38 http://us.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]             
Get:39 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                  
Get:40 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]             
Get:41 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]              
Get:42 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                             
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                       
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                       
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                         
Get:43 http://us.archive.ubuntu.com precise-updates/restricted Sources [2,073 B]           
Get:44 http://us.archive.ubuntu.com precise-updates/main Sources [141 kB]                  
Get:45 http://us.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]           
Get:46 http://us.archive.ubuntu.com precise-updates/universe Sources [43.8 kB]             
Get:47 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [341 kB]           
Get:48 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [3,933 B]    
Get:49 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [112 kB]       
Get:50 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [2,365 B]    
Get:51 http://us.archive.ubuntu.com precise-updates/main i386 Packages [344 kB]            
Get:52 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [3,949 B]     
Get:53 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [113 kB]        
Get:54 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,540 B]     
Get:55 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]        
Get:56 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]  
Get:57 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]  
Get:58 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]    
Hit http://us.archive.ubuntu.com precise/main Translation-en                               
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                         
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                         
Hit http://us.archive.ubuntu.com precise/universe Translation-en                           
Get:59 http://us.archive.ubuntu.com precise-updates/main Translation-en [163 kB]           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                 
Get:60 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [1,083 B]    
Get:61 http://us.archive.ubuntu.com precise-updates/universe Translation-en [67.8 kB]      
Fetched 20.4 MB in 30s (677 kB/s)                                                          
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem)

```I need to run it manually? My friend didn't mention about needing to this, but whatever. Do what the system says, right? (BTW, the "--" before "configure" is two dashes, as the post editor  here seems to show them as one contiguous one.)

```

sudo dpkg --configure -a
Setting up kde-zeroconf (4:4.8.4-0ubuntu0.1) ...
Setting up libxinerama1:i386 (2:1.1.1-3build1) ...
Setting up libgd2-xpm:i386 (2.0.36~rc1~dfsg-6ubuntu2) ...
Setting up libnepomukdatamanagement4 (4:4.8.4-0ubuntu0.1) ...
Setting up libcupsmime1 (1.5.3-0ubuntu1) ...
Setting up system-config-printer-udev (1.3.8+20120201-0ubuntu8.1) ...
Setting up libcupsdriver1 (1.5.3-0ubuntu1) ...
Setting up libqt4-network (4:4.8.1-0ubuntu4.1) ...
Setting up libqt4-script (4:4.8.1-0ubuntu4.1) ...
dpkg: error processing libtiff4 (--configure):
 libtiff4:amd64 3.9.5-2ubuntu1.1 cannot be configured because libtiff4:i386 is in a different version (3.9.5-2ubuntu1.2)
dpkg: error processing libtiff4:i386 (--configure):
 libtiff4:i386 3.9.5-2ubuntu1.2 cannot be configured because libtiff4:amd64 is in a different version (3.9.5-2ubuntu1.1)
Setting up smbclient (2:3.6.3-2ubuntu2.3) ...
Setting up libxdamage1:i386 (1:1.1.3-2build1) ...
Setting up libksgrd4 (4:4.8.4a-0ubuntu0.1) ...
dpkg: dependency problems prevent configuration of okular-extra-backends:
 okular-extra-backends depends on libtiff4; however:
  Package libtiff4 is not configured yet.
dpkg: error processing okular-extra-backends (--configure):
 dependency problems - leaving unconfigured
Setting up libheimntlm0-heimdal:i386 (1.6~git20120311.dfsg.1-2) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.3) ...
Setting up qdbus (4:4.8.1-0ubuntu4.1) ...
Setting up libgssapi3-heimdal:i386 (1.6~git20120311.dfsg.1-2) ...
Setting up libcupscgi1 (1.5.3-0ubuntu1) ...
Setting up libgphoto2-2:i386 (2.4.13-1ubuntu1) ...
Setting up libldap-2.4-2:i386 (2.4.28-1.1ubuntu4) ...
Setting up libcupsppdc1 (1.5.3-0ubuntu1) ...
Setting up libsolidcontrol4abi2 (4:4.8.4a-0ubuntu0.1) ...
Setting up libxxf86vm1:i386 (1:1.1.1-2build1) ...
Setting up libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.1) ...
Setting up libqt4-xmlpatterns (4:4.8.1-0ubuntu4.1) ...
Setting up libxcursor1:i386 (1:1.1.12-1) ...
dpkg: dependency problems prevent configuration of libcupsimage2:
 libcupsimage2 depends on libtiff4; however:
  Package libtiff4 is not configured yet.
dpkg: error processing libcupsimage2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups:
 cups depends on libcupsimage2 (>= 1.4.0); however:
  Package libcupsimage2 is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on libtiff4; however:
  Package libtiff4:i386 is not configured yet.
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up cups-ppdc (1.5.3-0ubuntu1) ...
dpkg: dependency problems prevent configuration of kdegraphics-strigi-analyzer:
 kdegraphics-strigi-analyzer depends on libtiff4; however:
  Package libtiff4 is not configured yet.
dpkg: error processing kdegraphics-strigi-analyzer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on libtiff4; however:
  Package libtiff4 is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dolphin:
 dolphin depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing dolphin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdemultimedia-kio-plugins:
 kdemultimedia-kio-plugins depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kdemultimedia-kio-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq5abi1:
 libkonq5abi1 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkonq5abi1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libokularcore1abi1:
 libokularcore1abi1 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libokularcore1abi1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-widgets-addons:
 plasma-widgets-addons depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing plasma-widgets-addons (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkephal4abi1:
 libkephal4abi1 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkephal4abi1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kppp:
 kppp depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kppp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-widgets-workspace:
 plasma-widgets-workspace depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing plasma-widgets-workspace (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-style-oxygen:
 kde-style-oxygen depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kde-style-oxygen (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
Setting up libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.1) ...
dpkg: dependency problems prevent configuration of libqt4-declarative:
 libqt4-declarative depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-declarative (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-dataengines-addons:
 plasma-dataengines-addons depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing plasma-dataengines-addons (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-client:
 cups-client depends on libcupsimage2 (>= 1.4.0); however:
  Package libcupsimage2 is not configured yet.
dpkg: error processing cups-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kate:
 kate depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkworkspace4abi1:
 libkworkspace4abi1 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkworkspace4abi1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtaskmanager4abi3:
 libtaskmanager4abi3 depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 libtaskmanager4abi3 depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libtaskmanager4abi3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libksignalplotter4:
 libksignalplotter4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libksignalplotter4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcupsfilters1:
 libcupsfilters1 depends on libtiff4; however:
  Package libtiff4 is not configured yet.
dpkg: error processing libcupsfilters1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-netbook:
 plasma-netbook depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 plasma-netbook depends on libqtgui4 (>= 4:4.6.2); however:
  Package libqtgui4 is not configured yet.
 plasma-netbook depends on plasma-widgets-workspace (= 4:4.8.4a-0ubuntu0.1); however:
  Package plasma-widgets-workspace is not configured yet.
dpkg: error processing plasma-netbook (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkcddb4:
 libkcddb4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkcddb4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gwenview:
 gwenview depends on libkonq5abi1 (>= 4:4.6.1); however:
  Package libkonq5abi1 is not configured yet.
 gwenview depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg is not configured yet.
 gwenview depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing gwenview (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of katepart:
 katepart depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing katepart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkwineffects1abi3:
 libkwineffects1abi3 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkwineffects1abi3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmenuedit:
 kmenuedit depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kmenuedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kamera:
 kamera depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kamera (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcalc:
 kcalc depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kcalc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-dataengines-workspace:
 plasma-dataengines-workspace depends on libkworkspace4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkworkspace4abi1 is not configured yet.
 plasma-dataengines-workspace depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
 plasma-dataengines-workspace depends on libtaskmanager4abi3 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libtaskmanager4abi3 is not configured yet.
dpkg: error processing plasma-dataengines-workspace (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of okular:
 okular depends on libokularcore1abi1 (>= 4:4.7.95); however:
  Package libokularcore1abi1 is not configured yet.
 okular depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg is not configured yet.
 okular depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing okular (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkateinterfaces4:
 libkateinterfaces4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkateinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
dpkg: error processing software-properties-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-filters:
 cups-filters depends on libcupsfilters1 (>= 1.0~b1); however:
  Package libcupsfilters1 is not configured yet.
 cups-filters depends on libcupsimage2 (>= 1.4.0); however:
  Package libcupsimage2 is not configured yet.
dpkg: error processing cups-filters (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-scriptengine-python:
 plasma-scriptengine-python depends on python-kde4 (>= 4:4.6.80); however:
  Package python-kde4 is not configured yet.
dpkg: error processing plasma-scriptengine-python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-desktop:
 plasma-desktop depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 plasma-desktop depends on libkworkspace4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkworkspace4abi1 is not configured yet.
 plasma-desktop depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
 plasma-desktop depends on libtaskmanager4abi3 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libtaskmanager4abi3 is not configured yet.
 plasma-desktop depends on plasma-widgets-workspace (= 4:4.8.4a-0ubuntu0.1); however:
  Package plasma-widgets-workspace is not configured yet.
dpkg: error processing plasma-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkscreensaver5:
 libkscreensaver5 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkscreensaver5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksystemlog:
 ksystemlog depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing ksystemlog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-ptouch:
 printer-driver-ptouch depends on libcupsimage2 (>= 1.4.0); however:
  Package libcupsimage2 is not configured yet.
dpkg: error processing printer-driver-ptouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kinfocenter:
 kinfocenter depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kinfocenter (--configure):
 dependency problems - leaving unconfigured
Setting up libgl1-mesa-glx:i386 (8.0.2-0ubuntu3.1) ...
dpkg: dependency problems prevent configuration of libqt4-opengl:
 libqt4-opengl depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-opengl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasmaclock4abi3:
 libplasmaclock4abi3 depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 libplasmaclock4abi3 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libplasmaclock4abi3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libprocessui4a:
 libprocessui4a depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libprocessui4a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-widget-folderview:
 plasma-widget-folderview depends on libkonq5abi1 (>= 4:4.8.2); however:
  Package libkonq5abi1 is not configured yet.
 plasma-widget-folderview depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing plasma-widget-folderview (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ark:
 ark depends on libkonq5abi1 (>= 4:4.6.1); however:
  Package libkonq5abi1 is not configured yet.
 ark depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing ark (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libtiff4
 libtiff4:i386
 okular-extra-backends
 libcupsimage2
 cups
 libsane:i386
 kdegraphics-strigi-analyzer
 libqtgui4
 dolphin
 kdemultimedia-kio-plugins
 libkonq5abi1
 libokularcore1abi1
 plasma-widgets-addons
 libkephal4abi1
 kppp
 plasma-widgets-workspace
 kde-style-oxygen
 python-kde4
 libqt4-declarative
 plasma-dataengines-addons
 cups-client
 kate
 libkworkspace4abi1
 libqt4-svg
 libtaskmanager4abi3
 libksignalplotter4
 libcupsfilters1
 plasma-netbook
 libkcddb4
 gwenview
 katepart
 libkwineffects1abi3
 kmenuedit
 kamera
 kcalc
 plasma-dataengines-workspace
 okular
 libkateinterfaces4
 software-properties-kde
 cups-filters
 plasma-scriptengine-python
 plasma-desktop
 libkscreensaver5
 ksystemlog
 printer-driver-ptouch
 kinfocenter
 libqt4-opengl
 libplasmaclock4abi3
 libprocessui4a
 plasma-widget-folderview
 ark
Processing was halted because there were too many errors.)
```Hmm. Well this isn't good. How am I supposed to resolve the first problem I get using Terminal if this one doesn't? ;) Either these errors are the reason why  Muon is not installing any programs or they are another problem altogether.

Anyway, here's another command my friend told me to run after the "sudo apt-get update && sudo apt-get upgrade" command. I probably shouldn't have done so, due to the last error, but I'm relatively new to Linux & learning by trial & error.

```

sudo apt-get -f install

(Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libtiff4 ttf-mscorefonts-installer
The following packages will be upgraded:
  libtiff4 ttf-mscorefonts-installer
2 upgraded, 0 newly installed, 0 to remove and 203 not upgraded.
105 not fully installed or removed.
Need to get 171 kB of archives.
After this operation, 133 kB of additional disk space will be used.
Do you want to continue [Y/n]?

```I hit "Y" & then it does its thing, but then I'm presented with this:

```

(Package configuration                                                                       
                                                                                            
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; 
 &#9474;                                                                                        &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                                     
 &#9474;                                                                                          
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                                        
 &#9474;                                                                                          
 &#9474;                                                                                          
 &#9474;                                         <Ok>                                             
 &#9474;                                                                                        &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;)
 
```Then a bunch of typical legal jargon that you see with a software license follows if I scroll down, but since this is in Terminal, I can't click on the "Ok" that shows at the bottom and there's no other prompt to continue, so I don't know what this is supposed to do or if it was even done with whatever it was doing, so I just close the Terminal program.

Nevertheless, I tried installing a program in Muon again, in this case Pidgin. But I get the following error:

```

(Another application seems to be using the package system at this time. You must close all other managers before you will be able to install or remove any pakages.)

```Was this due to the "sudo apt-get install -f" command I had just run? Oh well, after a few attempts I was able to resolve this error, but I still get the same error message that I mentioned at the start when attempting to install Pidgin or any other program I chose in the manager.

Frustrated, I tried installing a program via the Terminal, in this case Pidgin.

```

sudo apt-get install pidgin

"Reading package lists... Done
Building dependency tree      
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libtiff4 : Breaks: libtiff4:i386 (!= 3.9.5-2ubuntu1.1) but 3.9.5-2ubuntu1.2 is to be installed
 libtiff4:i386 : Breaks: libtiff4 (!= 3.9.5-2ubuntu1.2) but 3.9.5-2ubuntu1.1 is to be installed
 pidgin : Depends: pidgin-data (>= 1:2.10.6) but it is not going to be installed
          Depends: pidgin-data (< 1:2.10.6-z) but it is not going to be installed
          Depends: libgtkspell0 (>= 2.0.10) but it is not going to be installed
          Depends: libpurple0 (>= 1:2.8.0) but it is not going to be installed
          Depends: gconf2 (>= 2.28.1-2)
          Recommends: pidgin-libnotify but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)."

```But all that would do is bring me to that EULA from Microsoft with seemingly no other way to continue. And what in the blue hell has Microsoft to do with Kubuntu, anyway?!?

In addition to the commands my friend suggested, he did mention that it may be the fact that I'm using a 64-bit OS & in his experience he's always stayed with 32-bit as the other is "prone to bugs & instability." Okay, whatever...he's just giving his personal opinion anyway & suggested I install 32-bit. Well if that's what I have to do, that's fine with me, but I see the problem I am having  as an excellent opportunity to learn how to resolve problems as they come up as well as how things work in the OS.  So can anyone out there throw me a bone? Thanks in advance for any information you can give me. :)

- IANO

---

### Post by IAmNoOne on 2012-08-01
Just a follow up, on a hunch I tried "sudo apt-get -f install pidgin as well, but the system only tells me to run the same command  without specifying a package "(or specify a solution)"...whatever "specify a solution" means.  Oh well, couldn't have hurt to try, I guess.

- IANO

---

### Post by oldos2er on 2012-08-01
To accept the EULA for ttf-mscorefonts-installer, hit Tab to highlight OK, then Enter.

Could you post your sources.list? ```
cat /etc/apt/sources.list
```

---

### Post by drmrgd on 2012-08-01
Seems to be a lot to tackle here.  I can certainly help with a couple of these:

1. The MS EULA thing is for the TTF fonts you are trying to install (perhaps from the restricted extras package?).  In order to accept, you need to hit the Tab key until 'OK' is highlighted.  Then you can accept.

2. There appears to be some oddities with the packages that the system wants to install.  Perhaps posting the output of:

```
cat /etc/apt/sources.list
``` 

might help clear up some of this.

3.  There is no issue with the 64-bit version of Ubuntu, and your friend is misinformed!  :)

Edit:  Wow!  Got beat to the punch by quite a lot.  Looks like I might need to take a typing class or something!

---

### Post by IAmNoOne on 2012-08-01
Thanks for the reply. Huh, I wouldn't have known to use the TAB key. Now I know. ("And knowing is half the battle." ;) )

Anyway, so I run the "sudo apt-get install -f" again...

```

sudo apt-get install -f
[sudo] password for dracoarum: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libtiff4 ttf-mscorefonts-installer
The following packages will be upgraded:
  libtiff4 ttf-mscorefonts-installer
2 upgraded, 0 newly installed, 0 to remove and 203 not upgraded.
102 not fully installed or removed.
Need to get 171 kB of archives.
After this operation, 133 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libtiff4 amd64 3.9.5-2ubuntu1.2 [144 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/multiverse ttf-mscorefonts-installer all 3.4ubuntu3 [27.4 kB]
Fetched 171 kB in 0s (204 kB/s)                   
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 121942 files and directories currently installed.)
Preparing to replace ttf-mscorefonts-installer 3.4ubuntu3 (using .../ttf-mscorefonts-installer_3.4ubuntu3_all.deb) ...
Unpacking replacement ttf-mscorefonts-installer ...
Processing triggers for fontconfig ...
Processing triggers for update-notifier-common ...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe                                                       
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/verdan32.exe                                                       
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/webdin32.exe                                                       
                                                                                                                                                     
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Extracting cabinet: /tmp/tmpURYfEe.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: /tmp/tmphshwBZ.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpp8fUs7.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpL6g6WU.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmp9ks5V1.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpT8hhmx.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: /tmp/tmpWTB7m4.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /tmp/tmpwW3Fxh.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: /tmp/tmp0qsAnv.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: /tmp/tmpoI9tQa.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: /tmp/tmpFUYJPk.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
dpkg: error processing libtiff4 (--configure):
 libtiff4:amd64 3.9.5-2ubuntu1.1 cannot be configured because libtiff4:i386 is in a different version (3.9.5-2ubuntu1.2)
dpkg: error processing libtiff4:i386 (--configure):
 libtiff4:i386 3.9.5-2ubuntu1.2 cannot be configured because libtiff4:amd64 is in a different version (3.9.5-2ubuntu1.1)
dpkg: dependency problems prevent configuration of libcupsfilters1:
 libcupsfilters1 depends on libtiff4; however:No apport report written because MaxReports is reached already

  Package libtiff4 is not configured yet.
dpkg: error processing libcupsfilters1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcupsimage2:
 libcupsimage2 depends on libtiff4; however:
  Package libtiff4 is not configured yet.
dpkg: error processing libcupsimage2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of cups-filters:
 cups-filters depends on libcupsfilters1 (>= 1.0~b1); however:
  Package libcupsfilters1 is not configured yet.
 cups-filters depends on libcupsimage2 (>= 1.4.0); however:
  Package libcupsimage2 is not configured yet.
dpkg: error processing cups-filters (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups-client:
 cups-client depends on libcupsimage2 (>= 1.4.0); however:
  Package libcupsimage2 is not configured yet.
dpkg: error processing cups-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups:
 cups depends on libcupsimage2 (>= 1.4.0); however:
  Package libcupsimage2 is not configured yet.
 cups depends on cups-client (>= 1.5.3-0ubuntu1); however:
  Package cups-client is not configured yet.
 cups depends on cups-filters; however:
  Package cups-filters is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on libtiff4; however:
  Package libtiff4 is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:
 libqt4-declarative depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-declarative (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                                                                                                   dpkg: dependency problems prevent configuration of libqt4-help:
 libqt4-help depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-help (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:
 libqt4-opengl depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-opengl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4:4.8.1-0ubuntu4.1); however:
  Package libqt4-designer is not configured yet.
 libqt4-qt3support depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                     dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-scripttools:
 libqt4-scripttools depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-scripttools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on libtiff4; however:
  Package libtiff4:i386 is not configured yet.
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-mscorefonts-installer (3.4ubuntu3) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of libkactivities-bin:
 libkactivities-bin depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkactivities-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-scriptengine-javascript:
 plasma-scriptengine-javascript depends on libqtgui4 (>= 4:4.6.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing plasma-scriptengine-javascript (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on libqt4-declarative (>= 4:4.7.0~rc1); however:
  Package libqt4-declarative is not configured yet.
 kde-runtime depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg is not configured yet.
 kde-runtime depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
 kde-runtime depends on pNo apport report written because MaxReports is reached already
                                                                                       No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                                                                                                   No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                                                                                                        No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                                                                                                               No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
                                                                                      lasma-scriptengine-javascript (= 4:4.8.4-0ubuntu0.1); however:
  Package plasma-scriptengine-javascript is not configured yet.
dpkg: error processing kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq-common:
 libkonq-common depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkonq-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq5abi1:
 libkonq5abi1 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
 libkonq5abi1 depends on libkonq-common (>= 4:4.8.4-0ubuntu0.1); however:
  Package libkonq-common is not configured yet.
dpkg: error processing libkonq5abi1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ark:
 ark depends on kde-runtime; however:
  Package kde-runtime is not configured yNo apport report written because MaxReports is reached already
                                                                                                       No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                                                                                                            No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                                                                                                   No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
                                                                                          et.
 ark depends on libkonq5abi1 (>= 4:4.6.1); however:
  Package libkonq5abi1 is not configured yet.
 ark depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing ark (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dolphin:
 dolphin depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 dolphin depends on libkonq5abi1 (>= 4:4.7.90); however:
  Package libkonq5abi1 is not configured yet.
 dolphin depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing dolphin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dragonplayer:
 dragonplayer depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 dragonplayer depends on libqtgui4 (>= 4:4.6.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing No apport report written because MaxReports is reached already
                                                                                     No apport report written because MaxReports is reached already
                                                                                                                                                   dragonplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freespacenotifier:
 freespacenotifier depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing freespacenotifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkipi8:
 libkipi8 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkipi8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gwenview:
 gwenview depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 gwenview depends on libkipi8 (>= 4:4.7.90); however:
  Package libkipi8 is not configured yet.
 gwenview depends on libkonq5abi1 (>= 4:4.6.1); however:
  Package libkonq5abi1 is not configured yet.
 gwenview depends on libqt4-opengl (>= 4:4.5.3); however:
  Package libqt4-opengl is not configured yet.
 gwenview depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg is not configured yet.
 gwenview depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing gwenview (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kamera:
 kamera depends on libqt4-qt3support (>= 4:4.5.3); however:
  Package libqt4-qt3support is not configured yet.
 kamera depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kamera (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkateinterfaces4:
 libkateinterfaces4 depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 libkateinterfaces4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkateinterfaces4 No apport report written because MaxReports is reached already
                                                                                                        (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkatepartinterfaces4:
 libkatepartinterfaces4 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkatepartinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of katepart:
 katepart depends on libkatepartinterfaces4; however:
  Package libkatepartinterfaces4 is not configured yet.
 katepart depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing katepart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kate:
 kate depends on katepart (= 4:4.8.4-0ubuntu0.1); however:
  Package katepart is not configured yet.
 kate depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kate depends on libkateinterfaces4; however:
  Package libkateinterfaces4 is not configured yet.
 kate depends on libqt4-qt3support (>= 4:4.5.3); however:
  Package libqt4-qt3support is not configured yet.
 kate depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcalc:
 kcalc depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kcalc depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kcalc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-baseapps-bin:
 kde-baseapps-bin depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-baseapps-bin depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kde-baseapps-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-style-oxygen:
 kde-style-oxygen depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-style-oxygen depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kde-style-oxygen (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdecorations4:
 libkdecorations4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkdecorations4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkephal4abi1:
 libkephal4abi1 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkephal4abi1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkwineffects1abi3:
 libkwineffects1abi3 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkwineffects1abi3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkworkspace4abi1:
 libkworkspace4abi1 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkworkspace4abi1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkactivities6:
 libkactivities6 depends on libkactivities-bin (= 4:4.8.4-0ubuntu0.1); however:
  Package libkactivities-bin is not configured yet.
dpkg: error processing libkactivities6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkwinglutils1:
 libkwinglutils1 depends on libqtgui4 (>= 4:4.6.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkwinglutils1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-window-manager-common:
 kde-window-manager-common depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager-common depends on kde-style-oxygen; however:
  Package kde-style-oxygen is not configured yet.
 kde-window-manager-common depends on libkdecorations4 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkdecorations4 is not configured yet.
 kde-window-manager-common depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 kde-window-manager-common depends on libkwineffects1abi3 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkwineffects1abi3 is not configured yet.
 kde-window-manager-common depends on libkworkspace4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkworkspace4abi1 is not configured yet.
 kde-window-manager-common depends on libqt4-declarative (>= 4:4.7.0~rc1); however:
  Package libqt4-declarative is not configured yet.
 kde-window-manager-common depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kde-window-manager-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-window-manager:
 kde-window-manager depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager depends on libkactivities6 (>= 4.7.90); however:
  Package libkactivities6 is not configured yet.
 kde-window-manager depends on libkdecorations4 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkdecorations4 is not configured yet.
 kde-window-manager depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 kde-window-manager depends on libkwineffects1abi3 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkwineffects1abi3 is not configured yet.
 kde-window-manager depends on libkwinglutils1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkwinglutils1 is not configured yet.
 kde-window-manager depends on libkworkspace4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkworkspace4abi1 is not configured yet.
 kde-window-manager depends on libqt4-declarative (>= 4:4.7.0~rc1); however:
  Package libqt4-declarative is not configured yet.
 kde-window-manager depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
 kde-window-manager depends on kde-window-manager-common (= 4:4.8.4a-0ubuntu0.1); however:
  Package kde-window-manager-common is not configured yet.
dpkg: error processing kde-window-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkscreensaver5:
 libkscreensaver5 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkscreensaver5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libplasmagenericshell4:
 libplasmagenericshell4 depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 libplasmagenericshell4 depends on libkworkspace4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkworkspace4abi1 is not configured yet.
 libplasmagenericshell4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libplasmagenericshell4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libprocessui4a:
 libprocessui4a depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libprocessui4a (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libtaskmanager4abi3:
 libtaskmanager4abi3 depends on libkactivities6 (>= 4.7.90); however:
  Package libkactivities6 is not configured yet.
 libtaskmanager4abi3 depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 libtaskmanager4abi3 depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libtaskmanager4abi3 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libplasmaclock4abi3:
 libplasmaclock4abi3 depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 libplasmaclock4abi3 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libplasmaclock4abi3 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plasma-dataengines-workspace:
 plasma-dataengines-workspace depends on libkworkspace4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkworkspace4abi1 is not configured yet.
 plasma-dataengines-workspace depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
 plasma-dataengines-workspace depends on libtaskmanager4abi3 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libtaskmanager4abi3 is not configured yet.
dpkg: error processing plasma-dataengines-workspace (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plasma-widgets-workspace:
 plasma-widgets-workspace depends on libkworkspace4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkworkspace4abi1 is not configured yet.
 plasma-widgets-workspace depends on libplasmaclock4abi3 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libplasmaclock4abi3 is not configured yet.
 plasma-widgets-workspace depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4 is not configured yet.
 plasma-widgets-workspace depends on plasma-dataengines-workspace (= 4:4.8.4a-0ubuntu0.1); however:
  Package plasma-dataengines-workspace is not configured yet.
dpkg: error processing plasma-widgets-workspace (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plasma-desktop:
 plasma-desktop depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 plasma-desktop depends on libkactivities6 (>= 4.7.90); however:
  Package libkactivities6 is not configured yet.
 plasma-desktop depends on libkephal4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkephal4abi1 is not configured yet.
 plasma-desktop depends on libkworkspace4abi1 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libkworkspace4abi1 is not configured yet.
 plasma-desktop depends on libplasmagenericshell4 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libplasmagenericshell4 is not configured yet.
 plasma-desktop depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
 plasma-desktop depends on libtaskmanager4abi3 (= 4:4.8.4a-0ubuntu0.1); however:
  Package libtaskmanager4abi3 is not configured yet.
 plasma-desktop depends on plasma-widgets-workspace (= 4:4.8.4a-0ubuntu0.1); however:
  Package plasma-widgets-workspace is not configured yet.
 plasma-desktop depends on libkactivities-bin; however:
  Package libkactivities-bin is not configured yet.
dpkg: error processing plasma-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libtiff4
 libtiff4:i386
 libcupsfilters1
 libcupsimage2
 cups-filters
 cups-client
 cups
 libqtgui4
 libqt4-declarative
 libqt4-designer
 libqt4-help
 libqt4-opengl
 libqt4-qt3support
 libqt4-scripttools
 libqt4-svg
 libsane:i386
 libkactivities-bin
 plasma-scriptengine-javascript
 kde-runtime
 libkonq-common
 libkonq5abi1
 ark
 dolphin
 dragonplayer
 freespacenotifier
 libkipi8
 gwenview
 kamera
 libkateinterfaces4
 libkatepartinterfaces4
 katepart
 kate
 kcalc
 kde-baseapps-bin
 kde-style-oxygen
 libkdecorations4
 libkephal4abi1
 libkwineffects1abi3
 libkworkspace4abi1
 libkactivities6
 libkwinglutils1
 kde-window-manager-common
 kde-window-manager
 libkscreensaver5
 libplasmagenericshell4
 libprocessui4a
 libtaskmanager4abi3
 libplasmaclock4abi3
 plasma-dataengines-workspace
 plasma-widgets-workspace
 plasma-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Same problem as before, but this time there's an "error code (1)" as you can see.  Here's the output of the other command suggested:

```

cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/

# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

So what does this tell you? Are you trying to see what I got on the system?

---

### Post by drmrgd on 2012-08-01
That libtiff error seems to be popping up in a few places today.  I had a look, and there is a bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/tiff/+bug/1021717](https://bugs.launchpad.net/ubuntu/+source/tiff/+bug/1021717)

It seems like there is a sync problem between the i386 and amd64 versions of the package.  Have a look at post #6, and see if that helps.  Be sure you go for the 64-bit version of that package instead of the 32-bit version listed, though:

```

cd /tmp
sudo apt-get download libtiff4 libtiff4:amd64
sudo dpkg -i libtiff4*deb

```

I can't test it out as I don't have 64-bit running on this computer.  Please report back if you get errors.

---

### Post by IAmNoOne on 2012-08-01
Thank you for your response, drmrgd.  I ran the code & whatever it did, it did it.

```

cd /tmp
 sudo apt-get download libtiff4 libtiff4:amd64
Get:1 Downloading libtiff4 3.9.5-2ubuntu1.2 [144 kB]
Fetched 1 B in 0s (4 B/s)          

```

```

sudo dpkg -i libtiff4*deb

(Reading database ... 123081 files and directories currently installed.)
Preparing to replace libtiff4 3.9.5-2ubuntu1.1 (using libtiff4_3.9.5-2ubuntu1.2_amd64.deb) ...
Unpacking replacement libtiff4 ...
Setting up libtiff4 (3.9.5-2ubuntu1.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Tested it out by installing pidgin on Muon & it worked! :D  Thank you so very much for your assistance, as well as the rest of you who posted in this thread. :D

So far so good, but If I have any other problems relating to this, I'll post a reply.

- IANO

---

### Post by drmrgd on 2012-08-01
Great!  I'm glad that worked.  We just forced it to download and install the 64-bit version of that library rather than letting apt make the decision for us.  Thanks to the poster over at the Launchpad Bug site for tip!

Anyway, glad you're back up and running.  To help others, please mark the thread as "Solved" using the Thread Tools drop-down at the top if you wouldn't mind.

---

