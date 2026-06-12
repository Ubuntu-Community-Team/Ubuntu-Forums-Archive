---
title: "Lubuntu wont install update"
date: 2012-02-27
forum: General Help
---

### Post by bOgNeR17 on 2012-02-27
For  the last couple of days I have been trying to update my lubuntu using the automatic update but it keeps failing for some reason. I have had no bother in the past installing updates either just this one.

---

### Post by ajgreeny on 2012-02-27
> **bOgNeR17 said:**
> For  the last couple of days I have been trying to update my lubuntu using the automatic update but it keeps failing for some reason. I have had no bother in the past installing updates either just this one.
Can you please run the commands ```
sudo apt-get update
sudo apt-get upgrade
``` and copy back any error messages you get.
Paste errors in a New Reply, then highlight it all and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.

---

### Post by bOgNeR17 on 2012-02-27
```
diarmuid@bognerdiarmuid1708920806000000000000:~$ sudo apt-get update
[sudo] password for diarmuid: 
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://ie.archive.ubuntu.com oneiric InRelease                             
Ign http://ie.archive.ubuntu.com oneiric-updates InRelease                     
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Ign http://ie.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ie.archive.ubuntu.com oneiric Release.gpg                           
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://ie.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ie.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://ie.archive.ubuntu.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://ie.archive.ubuntu.com oneiric-updates Release                       
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://ie.archive.ubuntu.com oneiric-backports Release                     
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://ie.archive.ubuntu.com oneiric/main Sources                          
Hit http://ie.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://ie.archive.ubuntu.com oneiric/universe Sources                      
Hit http://ie.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://ie.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://ie.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://ie.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://ie.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://ie.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://ie.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://ie.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://ie.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://ie.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://ie.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://ie.archive.ubuntu.com oneiric-updates/universe Sources              
Ign http://archive.getdeb.net oneiric-getdeb InRelease                         
Hit http://ie.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://ie.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://ie.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://ie.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://ie.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://ie.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://ie.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://ie.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://ie.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Ign http://extras.ubuntu.com oneiric/main Translation-en_IE                    
Hit http://ie.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://ie.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://ie.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://ie.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://ie.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://ie.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://ie.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://ie.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://ie.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://ie.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://ie.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://ie.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://ie.archive.ubuntu.com oneiric/main Translation-en         
Hit http://ie.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://ie.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://ie.archive.ubuntu.com oneiric/universe Translation-en     
Hit http://ie.archive.ubuntu.com oneiric-updates/main Translation-en 
Hit http://ie.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://ie.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://ie.archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_IE          
Hit http://ie.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://ie.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://ie.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://ie.archive.ubuntu.com oneiric-backports/universe Translation-en     
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_IE     
Ign http://ppa.launchpad.net oneiric/main Translation-en        
Get:1 http://archive.getdeb.net oneiric-getdeb Release.gpg [836 B]
Get:2 http://archive.getdeb.net oneiric-getdeb Release [7,244 B]
Ign http://archive.getdeb.net oneiric-getdeb Release
Ign http://archive.getdeb.net oneiric-getdeb/games Sources/DiffIndex           
Ign http://archive.getdeb.net oneiric-getdeb/games i386 Packages/DiffIndex     
Ign http://archive.getdeb.net oneiric-getdeb/games TranslationIndex            
Hit http://archive.getdeb.net oneiric-getdeb/games Sources                     
Hit http://archive.getdeb.net oneiric-getdeb/games i386 Packages               
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en_IE           
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en
Fetched 8,080 B in 29s (269 B/s)
Reading package lists... Done
W: GPG error: http://archive.getdeb.net oneiric-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
diarmuid@bognerdiarmuid1708920806000000000000:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra
  flashplugin-installer icedtea-6-jre-cacao icedtea-6-jre-jamvm openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib python-httplib2
  python-pkg-resources
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 57.5 MB/57.5 MB of archives.
After this operation, 856 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/universe chromium-browser-l10n all 17.0.963.56~r121963-0ubuntu0.11.10.1 [2,013 kB]
Get:2 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/universe chromium-codecs-ffmpeg-extra i386 17.0.963.56~r121963-0ubuntu0.11.10.1 [652 kB]
Get:3 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/universe chromium-browser i386 17.0.963.56~r121963-0ubuntu0.11.10.1 [20.2 MB]
Get:4 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/main icedtea-6-jre-cacao i386 6b23~pre11-0ubuntu1.11.10.2 [417 kB]
Get:5 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/main openjdk-6-jre-lib all 6b23~pre11-0ubuntu1.11.10.2 [6,090 kB]
Get:6 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/main icedtea-6-jre-jamvm i386 6b23~pre11-0ubuntu1.11.10.2 [528 kB]
Get:7 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/main openjdk-6-jre-headless i386 6b23~pre11-0ubuntu1.11.10.2 [27.3 MB]
Get:8 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/main openjdk-6-jre i386 6b23~pre11-0ubuntu1.11.10.2 [232 kB]
Get:9 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/main python-httplib2 all 0.7.2-1ubuntu2~0.11.10.1 [57.1 kB]
Get:10 http://ie.archive.ubuntu.com/ubuntu/ oneiric-updates/main python-pkg-resources all 0.6.16-1ubuntu0.1 [62.7 kB]
Fetched 57.5 MB in 5min 16s (182 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 182698 files and directories currently installed.)
Preparing to replace flashplugin-installer 11.1.102.62ubuntu0.11.10.1 (using .../flashplugin-installer_11.1.102.62ubuntu0.11.10.2_i386.deb) ...
update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt: line not terminated while trying to read status
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt: line not terminated while trying to read status
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_11.1.102.62ubuntu0.11.10.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Downloading...
--2012-02-27 23:27:05--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.62.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33, 91.189.92.191
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13785778 (13M) [application/x-gzip]
Saving to: `./adobe-flashplugin_11.1.102.62.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  0%  166K 81s
    50K .......... .......... .......... .......... ..........  0%  227K 70s
   100K .......... .......... .......... .......... ..........  1%  186K 70s
   150K .......... .......... .......... .......... ..........  1%  227K 67s
   200K .......... .......... .......... .......... ..........  1%  175K 68s
   250K .......... .......... .......... .......... ..........  2%  238K 66s
   300K .......... .......... .......... .......... ..........  2%  238K 64s
   350K .......... .......... .......... .......... ..........  2%  231K 63s
   400K .......... .......... .......... .......... ..........  3%  217K 63s
   450K .......... .......... .......... .......... ..........  3%  238K 62s
   500K .......... .......... .......... .......... ..........  4%  231K 61s
   550K .......... .......... .......... .......... ..........  4%  232K 60s
   600K .......... .......... .......... .......... ..........  4%  243K 59s
   650K .......... .......... .......... .......... ..........  5%  232K 59s
   700K .......... .......... .......... .......... ..........  5% 42.3K 75s
   750K .......... .......... .......... .......... ..........  5%  652K 71s
   800K .......... .......... .......... .......... ..........  6% 2.03M 67s
   850K .......... .......... .......... .......... ..........  6% 21.3M 63s
   900K .......... .......... .......... .......... ..........  7% 1.43M 60s
   950K .......... .......... .......... .......... ..........  7% 13.5M 57s
  1000K .......... .......... .......... .......... ..........  7%  236K 56s
  1050K .......... .......... .......... .......... ..........  8%  231K 56s
  1100K .......... .......... .......... .......... ..........  8%  163K 57s
  1150K .......... .......... .......... .......... ..........  8%  196K 57s
  1200K .......... .......... .......... .......... ..........  9%  230K 56s
  1250K .......... .......... .......... .......... ..........  9%  237K 56s
  1300K .......... .......... .......... .......... .......... 10%  229K 55s
  1350K .......... .......... .......... .......... .......... 10%  226K 55s
  1400K .......... .......... .......... .......... .......... 10%  225K 55s
  1450K .......... .......... .......... .......... .......... 11%  235K 55s
  1500K .......... .......... .......... .......... .......... 11%  229K 54s
  1550K .......... .......... .......... .......... .......... 11%  207K 54s
  1600K .......... .......... .......... .......... .......... 12%  184K 54s
  1650K .......... .......... .......... .......... .......... 12%  217K 54s
  1700K .......... .......... .......... .......... .......... 12%  236K 54s
  1750K .......... .......... .......... .......... .......... 13%  210K 53s
  1800K .......... .......... .......... .......... .......... 13%  225K 53s
  1850K .......... .......... .......... .......... .......... 14%  217K 53s
  1900K .......... .......... .......... .......... .......... 14%  196K 53s
  1950K .......... .......... .......... .......... .......... 14%  222K 53s
  2000K .......... .......... .......... .......... .......... 15%  236K 52s
  2050K .......... .......... .......... .......... .......... 15%  212K 52s
  2100K .......... .......... .......... .......... .......... 15%  236K 52s
  2150K .......... .......... .......... .......... .......... 16%  221K 52s
  2200K .......... .......... .......... .......... .......... 16%  235K 51s
  2250K .......... .......... .......... .......... .......... 17%  236K 51s
  2300K .......... .......... .......... .......... .......... 17%  228K 51s
  2350K .......... .......... .......... .......... .......... 17%  233K 50s
  2400K .......... .......... .......... .......... .......... 18%  236K 50s
  2450K .......... .......... .......... .......... .......... 18%  228K 50s
  2500K .......... .......... .......... .......... .......... 18%  235K 50s
  2550K .......... .......... .......... .......... .......... 19%  237K 49s
  2600K .......... .......... .......... .......... .......... 19%  231K 49s
  2650K .......... .......... .......... .......... .......... 20%  213K 49s
  2700K .......... .......... .......... .......... .......... 20%  236K 49s
  2750K .......... .......... .......... .......... .......... 20%  230K 48s
  2800K .......... .......... .......... .......... .......... 21%  236K 48s
  2850K .......... .......... .......... .......... .......... 21%  231K 48s
  2900K .......... .......... .......... .......... .......... 21%  237K 47s
  2950K .......... .......... .......... .......... .......... 22%  236K 47s
  3000K .......... .......... .......... .......... .......... 22%  230K 47s
  3050K .......... .......... .......... .......... .......... 23%  236K 47s
  3100K .......... .......... .......... .......... .......... 23%  236K 46s
  3150K .......... .......... .......... .......... .......... 23%  230K 46s
  3200K .......... .......... .......... .......... .......... 24%  236K 46s
  3250K .......... .......... .......... .......... .......... 24%  237K 46s
  3300K .......... .......... .......... .......... .......... 24%  230K 45s
  3350K .......... .......... .......... .......... .......... 25%  237K 45s
  3400K .......... .......... .......... .......... .......... 25%  237K 45s
  3450K .......... .......... .......... .......... .......... 25%  230K 45s
  3500K .......... .......... .......... .......... .......... 26%  237K 44s
  3550K .......... .......... .......... .......... .......... 26%  229K 44s
  3600K .......... .......... .......... .......... .......... 27%  236K 44s
  3650K .......... .......... .......... .......... .......... 27%  237K 44s
  3700K .......... .......... .......... .......... .......... 27%  228K 43s
  3750K .......... .......... .......... .......... .......... 28%  213K 43s
  3800K .......... .......... .......... .......... .......... 28%  239K 43s
  3850K .......... .......... .......... .......... .......... 28%  231K 43s
  3900K .......... .......... .......... .......... .......... 29%  192K 43s
  3950K .......... .......... .......... .......... .......... 29%  238K 42s
  4000K .......... .......... .......... .......... .......... 30%  230K 42s
  4050K .......... .......... .......... .......... .......... 30%  190K 42s
  4100K .......... .......... .......... .......... .......... 30%  217K 42s
  4150K .......... .......... .......... .......... .......... 31%  243K 41s
  4200K .......... .......... .......... .......... .......... 31%  163K 41s
  4250K .......... .......... .......... .......... .......... 31%  226K 41s
  4300K .......... .......... .......... .......... .......... 32%  238K 41s
  4350K .......... .......... .......... .......... .......... 32%  136K 41s
  4400K .......... .......... .......... .......... .......... 33%  234K 41s
  4450K .......... .......... .......... .......... .......... 33%  192K 41s
  4500K .......... .......... .......... .......... .......... 33%  126K 41s
  4550K .......... .......... .......... .......... .......... 34%  229K 40s
  4600K .......... .......... .......... .......... .......... 34% 86.0K 41s
  4650K .......... .......... .......... .......... .......... 34%  260K 41s
  4700K .......... .......... .......... .......... .......... 35%  221K 40s
  4750K .......... .......... .......... .......... .......... 35% 61.9K 41s
  4800K .......... .......... .......... .......... .......... 36% 12.5K 48s
  4850K .......... .......... .......... .......... .......... 36% 22.5K 51s
  4900K .......... .......... .......... .......... .......... 36%  135K 51s
  4950K .......... .......... .......... .......... .......... 37% 61.7K 51s
  5000K .......... .......... .......... .......... .......... 37%  194K 51s
  5050K .......... .......... .......... .......... .......... 37%  241K 50s
  5100K .......... .......... .......... .......... .......... 38%  230K 50s
  5150K .......... .......... .......... .......... .......... 38%  238K 49s
  5200K .......... .......... .......... .......... .......... 38%  238K 49s
  5250K .......... .......... .......... .......... .......... 39%  232K 49s
  5300K .......... .......... .......... .......... .......... 39%  238K 48s
  5350K .......... .......... .......... .......... .......... 40%  238K 48s
  5400K .......... .......... .......... .......... .......... 40%  231K 47s
  5450K .......... .......... .......... .......... .......... 40%  238K 47s
  5500K .......... .......... .......... .......... .......... 41%  231K 46s
  5550K .......... .......... .......... .......... .......... 41%  238K 46s
  5600K .......... .......... .......... .......... .......... 41%  238K 46s
  5650K .......... .......... .......... .......... .......... 42%  232K 45s
  5700K .......... .......... .......... .......... .......... 42%  238K 45s
  5750K .......... .......... .......... .......... .......... 43%  233K 44s
  5800K .......... .......... .......... .......... .......... 43%  237K 44s
  5850K .......... .......... .......... .......... .......... 43%  237K 44s
  5900K .......... .......... .......... .......... .......... 44%  238K 43s
  5950K .......... .......... .......... .......... .......... 44%  231K 43s
  6000K .......... .......... .......... .......... .......... 44%  238K 42s
  6050K .......... .......... .......... .......... .......... 45%  174K 42s
  6100K .......... .......... .......... .......... .......... 45%  356K 42s
  6150K .......... .......... .......... .......... .......... 46%  237K 41s
  6200K .......... .......... .......... .......... .......... 46%  230K 41s
  6250K .......... .......... .......... .......... .......... 46%  237K 41s
  6300K .......... .......... .......... .......... .......... 47%  236K 40s
  6350K .......... .......... .......... .......... .......... 47%  232K 40s
  6400K .......... .......... .......... .......... .......... 47%  233K 40s
  6450K .......... .......... .......... .......... .......... 48%  238K 39s
  6500K .......... .......... .......... .......... .......... 48%  228K 39s
  6550K .......... .......... .......... .......... .......... 49%  238K 39s
  6600K .......... .......... .......... .......... .......... 49%  235K 38s
  6650K .......... .......... .......... .......... .......... 49%  231K 38s
  6700K .......... .......... .......... .......... .......... 50%  234K 37s
  6750K .......... .......... .......... .......... .......... 50%  230K 37s
  6800K .......... .......... .......... .......... .......... 50%  238K 37s
  6850K .......... .......... .......... .......... .......... 51%  238K 36s
  6900K .......... .......... .......... .......... .......... 51%  231K 36s
  6950K .......... .......... .......... .......... .......... 51%  238K 36s
  7000K .......... .......... .......... .......... .......... 52%  234K 35s
  7050K .......... .......... .......... .......... .......... 52%  233K 35s
  7100K .......... .......... .......... .......... .......... 53%  238K 35s
  7150K .......... .......... .......... .......... .......... 53%  238K 34s
  7200K .......... .......... .......... .......... .......... 53%  231K 34s
  7250K .......... .......... .......... .......... .......... 54%  237K 34s
  7300K .......... .......... .......... .......... .......... 54%  230K 33s
  7350K .......... .......... .......... .......... .......... 54%  236K 33s
  7400K .......... .......... .......... .......... .......... 55%  238K 33s
  7450K .......... .......... .......... .......... .......... 55%  229K 32s
  7500K .......... .......... .......... .......... .......... 56%  238K 32s
  7550K .......... .......... .......... .......... .......... 56%  236K 32s
  7600K .......... .......... .......... .......... .......... 56%  230K 32s
  7650K .......... .......... .......... .......... .......... 57%  235K 31s
  7700K .......... .......... .......... .......... .......... 57%  232K 31s
  7750K .......... .......... .......... .......... .......... 57%  237K 31s
  7800K .......... .......... .......... .......... .......... 58%  237K 30s
  7850K .......... .......... .......... .......... .......... 58%  238K 30s
  7900K .......... .......... .......... .......... .......... 59%  230K 30s
  7950K .......... .......... .......... .......... .......... 59%  236K 29s
  8000K .......... .......... .......... .......... .......... 59%  231K 29s
  8050K .......... .......... .......... .......... .......... 60%  236K 29s
  8100K .......... .......... .......... .......... .......... 60%  232K 28s
  8150K .......... .......... .......... .......... .......... 60%  231K 28s
  8200K .......... .......... .......... .......... .......... 61%  237K 28s
  8250K .......... .......... .......... .......... .......... 61%  238K 28s
  8300K .......... .......... .......... .......... .......... 62%  231K 27s
  8350K .......... .......... .......... .......... .......... 62%  236K 27s
  8400K .......... .......... .......... .......... .......... 62%  238K 27s
  8450K .......... .......... .......... .......... .......... 63%  230K 26s
  8500K .......... .......... .......... .......... .......... 63%  237K 26s
  8550K .......... .......... .......... .......... .......... 63%  237K 26s
  8600K .......... .......... .......... .......... .......... 64%  229K 25s
  8650K .......... .......... .......... .......... .......... 64%  237K 25s
  8700K .......... .......... .......... .......... .......... 64%  230K 25s
  8750K .......... .......... .......... .......... .......... 65%  237K 25s
  8800K .......... .......... .......... .......... .......... 65%  237K 24s
  8850K .......... .......... .......... .......... .......... 66%  231K 24s
  8900K .......... .......... .......... .......... .......... 66%  237K 24s
  8950K .......... .......... .......... .......... .......... 66%  237K 23s
  9000K .......... .......... .......... .......... .......... 67%  231K 23s
  9050K .......... .......... .......... .......... .......... 67%  236K 23s
  9100K .......... .......... .......... .......... .......... 67%  234K 23s
  9150K .......... .......... .......... .......... .......... 68%  230K 22s
  9200K .......... .......... .......... .......... .......... 68%  238K 22s
  9250K .......... .......... .......... .......... .......... 69%  230K 22s
  9300K .......... .......... .......... .......... .......... 69%  237K 21s
  9350K .......... .......... .......... .......... .......... 69%  237K 21s
  9400K .......... .......... .......... .......... .......... 70%  230K 21s
  9450K .......... .......... .......... .......... .......... 70%  237K 21s
  9500K .......... .......... .......... .......... .......... 70%  237K 20s
  9550K .......... .......... .......... .......... .......... 71%  231K 20s
  9600K .......... .......... .......... .......... .......... 71%  237K 20s
  9650K .......... .......... .......... .......... .......... 72%  237K 19s
  9700K .......... .......... .......... .......... .......... 72%  230K 19s
  9750K .......... .......... .......... .......... .......... 72%  237K 19s
  9800K .......... .......... .......... .......... .......... 73%  237K 19s
  9850K .......... .......... .......... .......... .......... 73%  230K 18s
  9900K .......... .......... .......... .......... .......... 73%  237K 18s
  9950K .......... .......... .......... .......... .......... 74%  230K 18s
 10000K .......... .......... .......... .......... .......... 74%  233K 18s
 10050K .......... .......... .......... .......... .......... 75%  241K 17s
 10100K .......... .......... .......... .......... .......... 75%  230K 17s
 10150K .......... .......... .......... .......... .......... 75%  237K 17s
 10200K .......... .......... .......... .......... .......... 76%  237K 16s
 10250K .......... .......... .......... .......... .......... 76%  225K 16s
 10300K .......... .......... .......... .......... .......... 76%  234K 16s
 10350K .......... .......... .......... .......... .......... 77%  238K 16s
 10400K .......... .......... .......... .......... .......... 77%  228K 15s
 10450K .......... .......... .......... .......... .......... 77%  213K 15s
 10500K .......... .......... .......... .......... .......... 78%  207K 15s
 10550K .......... .......... .......... .......... .......... 78%  195K 15s
 10600K .......... .......... .......... .......... .......... 79%  220K 14s
 10650K .......... .......... .......... .......... .......... 79%  188K 14s
 10700K .......... .......... .......... .......... .......... 79%  182K 14s
 10750K .......... .......... .......... .......... .......... 80%  184K 14s
 10800K .......... .......... .......... .......... .......... 80%  151K 13s
 10850K .......... .......... .......... .......... .......... 80%  153K 13s
 10900K .......... .......... .......... .......... .......... 81%  196K 13s
 10950K .......... .......... .......... .......... .......... 81%  177K 13s
 11000K .......... .......... .......... .......... .......... 82%  125K 12s
 11050K .......... .......... .......... .......... .......... 82%  167K 12s
 11100K .......... .......... .......... .......... .......... 82%  154K 12s
 11150K .......... .......... .......... .......... .......... 83%  217K 12s
 11200K .......... .......... .......... .......... .......... 83%  101K 11s
 11250K .......... .......... .......... .......... .......... 83%  205K 11s
 11300K .......... .......... .......... .......... .......... 84%  214K 11s
 11350K .......... .......... .......... .......... .......... 84%  115K 11s
 11400K .......... .......... .......... .......... .......... 85%  225K 10s
 11450K .......... .......... .......... .......... .......... 85%  155K 10s
 11500K .......... .......... .......... .......... .......... 85%  221K 10s
 11550K .......... .......... .......... .......... .......... 86%  187K 10s
 11600K .......... .......... .......... .......... .......... 86%  219K 9s
 11650K .......... .......... .......... .......... .......... 86%  157K 9s
 11700K .......... .......... .......... .......... .......... 87%  201K 9s
 11750K .......... .......... .......... .......... .......... 87%  199K 9s
 11800K .......... .......... .......... .......... .......... 88%  170K 8s
 11850K .......... .......... .......... .......... .......... 88%  161K 8s
 11900K .......... .......... .......... .......... .......... 88%  183K 8s
 11950K .......... .......... .......... .......... .......... 89%  153K 8s
 12000K .......... .......... .......... .......... .......... 89%  164K 7s
 12050K .......... .......... .......... .......... .......... 89%  141K 7s
 12100K .......... .......... .......... .......... .......... 90%  167K 7s
 12150K .......... .......... .......... .......... .......... 90%  208K 7s
 12200K .......... .......... .......... .......... .......... 90%  210K 6s
 12250K .......... .......... .......... .......... .......... 91%  180K 6s
 12300K .......... .......... .......... .......... .......... 91%  237K 6s
 12350K .......... .......... .......... .......... .......... 92%  213K 6s
 12400K .......... .......... .......... .......... .......... 92%  232K 5s
 12450K .......... .......... .......... .......... .......... 92%  228K 5s
 12500K .......... .......... .......... .......... .......... 93%  230K 5s
 12550K .......... .......... .......... .......... .......... 93%  220K 4s
 12600K .......... .......... .......... .......... .......... 93%  230K 4s
 12650K .......... .......... .......... .......... .......... 94%  235K 4s
 12700K .......... .......... .......... .......... .......... 94%  210K 4s
 12750K .......... .......... .......... .......... .......... 95%  229K 3s
 12800K .......... .......... .......... .......... .......... 95%  210K 3s
 12850K .......... .......... .......... .......... .......... 95%  220K 3s
 12900K .......... .......... .......... .......... .......... 96%  230K 3s
 12950K .......... .......... .......... .......... .......... 96%  196K 2s
 13000K .......... .......... .......... .......... .......... 96%  223K 2s
 13050K .......... .......... .......... .......... .......... 97%  230K 2s
 13100K .......... .......... .......... .......... .......... 97%  236K 2s
 13150K .......... .......... .......... .......... .......... 98%  231K 1s
 13200K .......... .......... .......... .......... .......... 98%  237K 1s
 13250K .......... .......... .......... .......... .......... 98%  235K 1s
 13300K .......... .......... .......... .......... .......... 99%  231K 1s
 13350K .......... .......... .......... .......... .......... 99%  232K 0s
 13400K .......... .......... .......... .......... .......... 99%  240K 0s
 13450K .......... ..                                         100%  239K=69s

2012-02-27 23:28:15 (194 KB/s) - `./adobe-flashplugin_11.1.102.62.orig.tar.gz' saved [13785778/13785778]

Download done.
Flash Plugin installed.
update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt: line not terminated while trying to read status
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Preparing to replace chromium-browser-l10n 16.0.912.77~r118311-0ubuntu0.11.10.1 (using .../chromium-browser-l10n_17.0.963.56~r121963-0ubuntu0.11.10.1_all.deb) ...
Unpacking replacement chromium-browser-l10n ...
Preparing to replace chromium-codecs-ffmpeg-extra 16.0.912.77~r118311-0ubuntu0.11.10.1 (using .../chromium-codecs-ffmpeg-extra_17.0.963.56~r121963-0ubuntu0.11.10.1_i386.deb) ...
Unpacking replacement chromium-codecs-ffmpeg-extra ...
Preparing to replace chromium-browser 16.0.912.77~r118311-0ubuntu0.11.10.1 (using .../chromium-browser_17.0.963.56~r121963-0ubuntu0.11.10.1_i386.deb) ...
Unpacking replacement chromium-browser ...
Preparing to replace icedtea-6-jre-cacao 6b23~pre11-0ubuntu1.11.10.1 (using .../icedtea-6-jre-cacao_6b23~pre11-0ubuntu1.11.10.2_i386.deb) ...
Unpacking replacement icedtea-6-jre-cacao ...
Preparing to replace openjdk-6-jre-lib 6b23~pre11-0ubuntu1.11.10.1 (using .../openjdk-6-jre-lib_6b23~pre11-0ubuntu1.11.10.2_all.deb) ...
Unpacking replacement openjdk-6-jre-lib ...
Preparing to replace icedtea-6-jre-jamvm 6b23~pre11-0ubuntu1.11.10.1 (using .../icedtea-6-jre-jamvm_6b23~pre11-0ubuntu1.11.10.2_i386.deb) ...
Unpacking replacement icedtea-6-jre-jamvm ...
Preparing to replace openjdk-6-jre-headless 6b23~pre11-0ubuntu1.11.10.1 (using .../openjdk-6-jre-headless_6b23~pre11-0ubuntu1.11.10.2_i386.deb) ...
Unpacking replacement openjdk-6-jre-headless ...
Preparing to replace openjdk-6-jre 6b23~pre11-0ubuntu1.11.10.1 (using .../openjdk-6-jre_6b23~pre11-0ubuntu1.11.10.2_i386.deb) ...
Unpacking replacement openjdk-6-jre ...
Preparing to replace python-httplib2 0.7.1-1ubuntu1 (using .../python-httplib2_0.7.2-1ubuntu2~0.11.10.1_all.deb) ...
Unpacking replacement python-httplib2 ...
Preparing to replace python-pkg-resources 0.6.16-1 (using .../python-pkg-resources_0.6.16-1ubuntu0.1_all.deb) ...
Unpacking replacement python-pkg-resources ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_11.1.102.62ubuntu0.11.10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
diarmuid@bognerdiarmuid1708920806000000000000:~$ 

```

---

### Post by plucky on 2012-02-28
> W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF

From a terminal,run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8A515F046D7E7CF
sudo apt-get update
sudo apt-get clean
sudo apt-get install -f
```

and see what happens.Post any errors.

Good luck

---

### Post by raja.genupula on 2012-02-28
+1 to above answer 
99% it will solve the issue .if its not 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

will do the job .

---

### Post by bOgNeR17 on 2012-02-28
```
2012-02-28 12:20:10 (180 KB/s) - `./adobe-flashplugin_11.1.102.62.orig.tar.gz' saved [13785778/13785778]

Download done.
Flash Plugin installed.
update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt: line not terminated while trying to read status
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_11.1.102.62ubuntu0.11.10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
diarmuid@bognerdiarmuid1708920806000000000000:~$ 

```

Got the above error at the end of all the command lines. Thanks for the help this far.;)

---

### Post by raja.genupula on 2012-02-28
```
sudo rm /var/cache/apt/archives/flashplugin-installer_11.1.102.62ubuntu0.11.10.2_i386.deb
```
```
sudo apt-get update
```
and try again

---

### Post by bOgNeR17 on 2012-02-28
```
diarmuid@bognerdiarmuid1708920806000000000000:~$ sudo rm /var/cache/apt/archives/flashplugin-installer_11.1.102.62ubuntu0.11.10.2_i386.deb
[sudo] password for diarmuid: 
diarmuid@bognerdiarmuid1708920806000000000000:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Ign http://ie.archive.ubuntu.com oneiric InRelease                             
Ign http://ie.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://ie.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ie.archive.ubuntu.com oneiric Release.gpg                           
Hit http://ie.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://ie.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://ie.archive.ubuntu.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://ie.archive.ubuntu.com oneiric-updates Release                       
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://ie.archive.ubuntu.com oneiric-backports Release                     
Hit http://ie.archive.ubuntu.com oneiric/main Sources                          
Hit http://ie.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://ie.archive.ubuntu.com oneiric/universe Sources                      
Hit http://ie.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://ie.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://ie.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://ie.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://ie.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://ie.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://ie.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://ie.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://ie.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://ie.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://ie.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://ie.archive.ubuntu.com oneiric-updates/universe Sources              
Ign http://archive.getdeb.net oneiric-getdeb InRelease                         
Hit http://ie.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://ie.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://ie.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://ie.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://ie.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://ie.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://ie.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://ie.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://ie.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://ie.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://ie.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://ie.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://ie.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://ie.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://ie.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Ign http://extras.ubuntu.com oneiric/main Translation-en_IE                    
Hit http://ie.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://ie.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://ie.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://ie.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://ie.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://ie.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Hit http://ie.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://ie.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://ie.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://ie.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://ie.archive.ubuntu.com oneiric-updates/main Translation-en 
Hit http://ie.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://ie.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://ie.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://ie.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://ie.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://ie.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://ie.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_IE          
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_IE
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://archive.getdeb.net oneiric-getdeb Release.gpg
Hit http://archive.getdeb.net oneiric-getdeb Release      
Hit http://archive.getdeb.net oneiric-getdeb/games Sources
Hit http://archive.getdeb.net oneiric-getdeb/games i386 Packages
Ign http://archive.getdeb.net oneiric-getdeb/games TranslationIndex
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en_IE
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en
Reading package lists... Done
diarmuid@bognerdiarmuid1708920806000000000000:~$ #
```

What do I do next I'm quite new to using the terminal to download/install software and updates.

---

### Post by plucky on 2012-02-28
> What do I do next I'm quite new to using the terminal to download/install software and updates. 

Run from the terminal ```
sudo apt-get upgrade
``` just to make sure there isn't any more upgrades to install. 


Good Luck

---

### Post by ajgreeny on 2012-02-28
Why the package **build-essential**?  The OP is not having trouble building a package from source, just installing flash from the repos.

As an alternative possibility, if you have installed firefox in your Lubuntu as I have, try using the firefox add-on flash-aid which will probably sort out any flash problems, and also install the most appropriate flash version for your system, which might be the beta from Adobe direct.

---

### Post by plucky on 2012-02-28
> Why the package build-essential? 

Yes incorrect command for this thread.

---

