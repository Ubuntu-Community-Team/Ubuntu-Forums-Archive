---
title: "I can't run 'sudo apt-get update' or install openjdk..."
date: 2011-10-15
forum: General Help
---

### Post by Acutical on 2011-10-15
sudo apt-get update error
```
acutical@Ronnie-PC:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release [1,347 B]                            
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://us.archive.ubuntu.com oneiric InRelease                      
Ign http://us.archive.ubuntu.com oneiric-updates InRelease           
Ign http://us.archive.ubuntu.com oneiric-backports InRelease         
Get:3 http://dl.google.com stable/main i386 Packages [1,199 B]       
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://dl.google.com stable/main TranslationIndex                
Hit http://us.archive.ubuntu.com oneiric Release.gpg                 
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://us.archive.ubuntu.com oneiric Release                     
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric-updates Release             
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Ign http://security.ubuntu.com oneiric-security/main TranslationIndex
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources      
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources  
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Ign http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en 
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Ign http://security.ubuntu.com oneiric-security/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign http://security.ubuntu.com oneiric-security/main Translation-en  
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_US
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_US
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_US
Ign http://security.ubuntu.com oneiric-security/universe Translation-en
Get:4 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,919 kB]
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Fetched 2,745 B in 4s (555 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
acutical@Ronnie-PC:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release [1,347 B]                            
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://us.archive.ubuntu.com oneiric InRelease                      
Ign http://us.archive.ubuntu.com oneiric-updates InRelease           
Ign http://us.archive.ubuntu.com oneiric-backports InRelease         
Get:3 http://dl.google.com stable/main i386 Packages [1,199 B]       
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://dl.google.com stable/main TranslationIndex                
Hit http://us.archive.ubuntu.com oneiric Release.gpg                 
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://us.archive.ubuntu.com oneiric Release                     
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric-updates Release             
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Ign http://security.ubuntu.com oneiric-security/main TranslationIndex
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources      
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources  
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Ign http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en 
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Ign http://security.ubuntu.com oneiric-security/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign http://security.ubuntu.com oneiric-security/main Translation-en  
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_US
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_US
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_US
Ign http://security.ubuntu.com oneiric-security/universe Translation-en
Get:4 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,919 kB]
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Fetched 2,745 B in 4s (555 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

OpenJDK error
```
acutical@Ronnie-PC:~$  sudo apt-get install openjdk-7-jre
[sudo] password for acutical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ca-certificates-java default-jre default-jre-headless icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icedtea-7-jre-jamvm icedtea-netx java-common
  libaccess-bridge-java libaccess-bridge-java-jni openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openjdk-7-jre-headless
  openjdk-7-jre-lib ttf-dejavu-extra tzdata-java
Suggested packages:
  equivs icedtea-plugin sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic
  ttf-sazanami-mincho ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts
  ttf-kannada-fonts ttf-bengali-fonts icedtea6-plugin
The following NEW packages will be installed:
  ca-certificates-java default-jre default-jre-headless icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icedtea-7-jre-jamvm icedtea-netx java-common
  libaccess-bridge-java libaccess-bridge-java-jni openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openjdk-7-jre
  openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java
0 upgraded, 18 newly installed, 0 to remove and 11 not upgraded.
Need to get 75.0 MB of archives.
After this operation, 206 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe openjdk-7-jre-lib all 7~b147-2.0~pre6-1ubuntu1 [5,116 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/main openjdk-6-jre-lib all 6b23~pre10-0ubuntu5 [6,089 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric/main tzdata-java i386 2011k-1 [134 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric/main java-common all 0.42ubuntu2 [62.4 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ oneiric/main openjdk-6-jre-headless i386 6b23~pre10-0ubuntu5 [27.3 MB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ oneiric/main default-jre-headless i386 1:1.6-42ubuntu2 [3,982 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ oneiric/main ca-certificates-java all 20110912ubuntu3 [8,098 B]
Get:8 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe openjdk-7-jre-headless i386 7~b147-2.0~pre6-1ubuntu1 [30.1 MB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libaccess-bridge-java all 1.26.2-6 [409 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libaccess-bridge-java-jni i386 1.26.2-6 [4,458 B]
Get:11 http://us.archive.ubuntu.com/ubuntu/ oneiric/main openjdk-6-jre i386 6b23~pre10-0ubuntu5 [232 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ oneiric/main default-jre i386 1:1.6-42ubuntu2 [874 B]
Get:13 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe openjdk-7-jre i386 7~b147-2.0~pre6-1ubuntu1 [224 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ oneiric/main ttf-dejavu-extra i386 2.33-1ubuntu1 [3,420 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ oneiric/main icedtea-6-jre-cacao i386 6b23~pre10-0ubuntu5 [417 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ oneiric/main icedtea-6-jre-jamvm i386 6b23~pre10-0ubuntu5 [528 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe icedtea-7-jre-jamvm i386 7~b147-2.0~pre6-1ubuntu1 [528 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ oneiric/main icedtea-netx i386 1.1.3-1ubuntu1 [465 kB]
Fetched 75.0 MB in 8min 46s (143 kB/s)                                         
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-lib_7~b147-2.0~pre6-1ubuntu1_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b23~pre10-0ubuntu5_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b23~pre10-0ubuntu5_i386.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-headless_7~b147-2.0~pre6-1ubuntu1_i386.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.33-1ubuntu1_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Please help? :(

---

### Post by imachavel on 2011-10-15
well it worked for me, so the command is still the same

I don't know, no idea at all. really sorry

---

### Post by effenberg0x0 on 2011-10-15
Try this:

```
sudo mkdir ~/lists.backup
sudo mv /var/lib/apt/lists/* ~/lists.backup
sudo apt-get update 
sudo apt-get install openjdk-7-jre
```

Please report back.

Effenberg

---

### Post by Acutical on 2011-10-15
I stoped at the 'sudo apt-get update' part, i still got an error. D:

```
acutical@Ronnie-PC:~$ sudo mkdir ~/lists.backup
[sudo] password for acutical: 
acutical@Ronnie-PC:~$ sudo mv /var/lib/apt/lists/* ~/lists.backup
acutical@Ronnie-PC:~$ sudo apt-get update 
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://us.archive.ubuntu.com oneiric InRelease                   
Ign http://us.archive.ubuntu.com oneiric-updates InRelease           
Ign http://us.archive.ubuntu.com oneiric-backports InRelease         
Get:2 http://dl.google.com stable Release [1,347 B]                  
Ign http://extras.ubuntu.com oneiric InRelease                                 
Get:3 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Get:4 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:5 http://dl.google.com stable/main i386 Packages [1,199 B]                 
Get:6 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Get:7 http://security.ubuntu.com oneiric-security Release [23.2 kB]            
Get:8 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Ign http://dl.google.com stable/main TranslationIndex                          
Get:9 http://extras.ubuntu.com oneiric Release [9,759 B]                       
Get:10 http://us.archive.ubuntu.com oneiric-backports Release.gpg [198 B]      
Get:11 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                  
Get:12 http://security.ubuntu.com oneiric-security/main Sources [14 B]         
Get:13 http://extras.ubuntu.com oneiric/main Sources [14 B]                    
Get:14 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]   
Get:15 http://security.ubuntu.com oneiric-security/universe Sources [14 B]     
Get:16 http://security.ubuntu.com oneiric-security/multiverse Sources [14 B]   
Get:17 http://security.ubuntu.com oneiric-security/main i386 Packages [14 B]   
Get:18 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:19 http://security.ubuntu.com oneiric-security/universe i386 Packages [14 B]
Get:20 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [14 B]
Ign http://security.ubuntu.com oneiric-security/main TranslationIndex          
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Get:21 http://us.archive.ubuntu.com oneiric-updates Release [24.2 kB]          
Get:22 http://extras.ubuntu.com oneiric/main i386 Packages [14 B]              
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Get:23 http://us.archive.ubuntu.com oneiric-backports Release [23.3 kB]        
Get:24 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://extras.ubuntu.com oneiric/main Translation-en                      
Ign http://dl.google.com stable/main Translation-en                           
Ign http://security.ubuntu.com oneiric-security/main Translation-en_US        
Ign http://security.ubuntu.com oneiric-security/main Translation-en
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_US
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_US
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_US
Ign http://security.ubuntu.com oneiric-security/universe Translation-en
Get:25 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]       
Get:26 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Get:27 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]        
Get:28 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]      
84% [26 Sources bzip2 0 B] [28 Packages 119 kB/1,226 kB 9%]         163 kB/s 6s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:29 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B] 
Get:30 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]  
Get:31 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Get:32 http://us.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]    
Get:33 http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]
Get:34 http://us.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Get:35 http://us.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]
Get:36 http://us.archive.ubuntu.com oneiric-updates/main Sources [2,033 B]     
Get:37 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [14 B]  
Get:38 http://us.archive.ubuntu.com oneiric-updates/universe Sources [1,361 B] 
Get:39 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [14 B]  
Get:40 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [5,310 B]
Get:41 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [14 B]
Get:42 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [1,981 B]
Get:43 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [14 B]
Get:44 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [72 B]
Get:45 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [70 B]
Get:46 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [70 B]
Get:47 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [72 B]
Get:48 http://us.archive.ubuntu.com oneiric-backports/main Sources [14 B]      
Get:49 http://us.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]
Get:50 http://us.archive.ubuntu.com oneiric-backports/universe Sources [14 B]  
Get:51 http://us.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]
Get:52 http://us.archive.ubuntu.com oneiric-backports/main i386 Packages [14 B]
Get:53 http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]
Get:54 http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages [14 B]
Get:55 http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]
Ign http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Ign http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Ign http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Get:56 http://us.archive.ubuntu.com oneiric/main Translation-en [701 kB]       
Get:57 http://us.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]
Get:58 http://us.archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]
Get:59 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB] 
Get:60 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [3,044 B]
99% [59 Translation-en bzip2 0 B] [Waiting for headers]             163 kB/s 0s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:61 http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en [14 B]
Get:62 http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en [14 B]
Get:63 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [1,474 B]
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Fetched 15.6 MB in 2min 17s (113 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
acutical@Ronnie-PC:~$ 

```

---

### Post by effenberg0x0 on 2011-10-15
Ok, new approach.
```

sudo rm -rf /var/lib/apt/lists/partial/*
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo mkdir ~/sources.list.d && sudo mv /etc/apt/sources.list.d/* ~/sources.list.d/
sudo sed -i s'/us.//g' /etc/apt/sources.list
sudo apt-get update

```

Effenberg

---

### Post by Acutical on 2011-10-15
Okay, that worked... Do i have to to that every time before i do sudo apt-get update?

and thanks, BTW.

---

### Post by effenberg0x0 on 2011-10-15
Hopefully not. In theory we just fixed it.

Regards,
Effenberg

---

### Post by Acutical on 2011-10-15
Okay. Thanks for your help. ;)

---

### Post by Stryker777 on 2012-03-12
Worked for me too when I could not do a do-release-upgrade.  Kept failing with "missing header". 
Thanks!

---

