---
title: "Need Emergency Help problem on kubuntu"
date: 2012-08-27
forum: General Help
---

### Post by Raihan004 on 2012-08-27
Today I install kubuntu 12.04 (64 bit) removing linux mint 12 .
but facing lot of problem . Can't Install media codec and any software .
If i wana install soft using terminal this following error showing 

```


raihan@raihan-desktop:~$ sudo apt-get install vlc
[sudo] password for raihan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ca-certificates-java : Depends: openjdk-6-jre-headless (>= 6b16-1.6.1-2) but it is not going to be installed or
                                 java6-runtime-headless
 gbrainy : Depends: liblaunchpad-integration1.0-cil (>= 0.1.33) but it is not going to be installed
 libavcodec-extra-53:i386 : Depends: libavutil-extra-51:i386 (< 4:0.7.6ubuntu0.11.10.1+medibuntu1-99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                            Depends: libfaac0:i386 but it is not going to be installed
                            Depends: libopencore-amrnb0:i386 but it is not going to be installed
                            Depends: libopencore-amrwb0:i386 but it is not going to be installed
                            Depends: libvpx0:i386 (>= 0.9.0) but it is not installable
                            Depends: libx264-116:i386 but it is not installable
                            Recommends: apport-hooks-medibuntu:i386 but it is not installable
 libavdevice53:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not going to be installed or
                               libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
 libavfilter2:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not going to be installed or
                              libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                     Depends: libswscale2:i386 (< 4:0.7.6-99) but it is not going to be installed or
                              libswscale-extra-2:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
 libavformat53:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not going to be installed or
                               libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
 openjdk-6-jre-headless:i386 : Depends: openjdk-6-jre-lib:i386 (>= 6b24-1.11.3-1ubuntu0.11.10.1)
                               Depends: ca-certificates-java:i386
                               Depends: libjpeg62:i386 but it is not going to be installed
 openjdk-6-jre-lib : Depends: openjdk-6-jre-headless (>= 6b17) but it is not going to be installed
 telepathy-idle:i386 : Depends: libssl1.0.0:i386 (>= 1.0.0) but it is not going to be installed
 telepathy-logger:i386 : Depends: libtelepathy-logger2:i386 (= 0.2.10-2) but 0.4.0-0ubuntu1 is to be installed
 vlc : Depends: vlc-nox (= 2.0.3-0ubuntu0.12.04.1) but it is not going to be installed
       Depends: libavcodec53 (>= 4:0.8-1~) but it is not going to be installed or
                libavcodec-extra-53 (>= 4:0.8-1~) but it is not going to be installed
       Depends: libavutil51 (>= 4:0.8-1~) but it is not going to be installed or
                libavutil-extra-51 (>= 4:0.8-1~) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
       Depends: libsdl1.2debian (>= 1.2.10-1) but it is not going to be installed
       Depends: libtar0 but it is not going to be installed
       Depends: libva-x11-1 (> 1.0.15~) but it is not going to be installed
       Depends: libva1 (> 1.0.15~) but it is not going to be installed
       Depends: libvlccore5 (>= 2.0.0) but it is not going to be installed
       Depends: libxcb-composite0 but it is not going to be installed
       Depends: libxcb-keysyms1 (>= 0.3.8) but it is not going to be installed
       Depends: libxcb-randr0 (>= 1.1) but it is not going to be installed
       Depends: libxcb-xv0 (>= 1.2) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.3-0ubuntu0.12.04.1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.3-0ubuntu0.12.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
raihan@raihan-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libwrap0:i386 libjson0:i386 icedtea-netx-common libgif4:i386 ubuntu-wallpapers-precise libflac8:i386 libasyncns0:i386
  libxtst6:i386 libpulse0:i386 libsndfile1:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ca-certificates-java gbrainy icedtea-6-jre-cacao icedtea-6-jre-cacao:i386 icedtea-6-jre-jamvm icedtea-6-jre-jamvm:i386
  libavcodec-extra-53:i386 libavdevice53:i386 libavfilter2:i386 libavformat53:i386 openjdk-6-jre-headless
  openjdk-6-jre-headless:i386 openjdk-6-jre-lib telepathy-idle:i386 telepathy-logger:i386
Suggested packages:
  libfaad0:i386 sun-java6-fonts fonts-ipafont-gothic fonts-ipafont-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts libnss-mdns:i386 sun-java6-fonts:i386 fonts-ipafont-gothic:i386 fonts-ipafont-mincho:i386
  ttf-wqy-microhei:i386 ttf-wqy-zenhei:i386 ttf-indic-fonts-core:i386 ttf-telugu-fonts:i386 ttf-oriya-fonts:i386
  ttf-kannada-fonts:i386 ttf-bengali-fonts:i386
The following NEW packages will be installed:
  icedtea-6-jre-cacao icedtea-6-jre-jamvm openjdk-6-jre-headless
The following packages will be upgraded:
  ca-certificates-java gbrainy icedtea-6-jre-cacao:i386 icedtea-6-jre-jamvm:i386 libavcodec-extra-53:i386 libavdevice53:i386
  libavfilter2:i386 libavformat53:i386 openjdk-6-jre-headless:i386 openjdk-6-jre-lib telepathy-idle:i386
  telepathy-logger:i386
12 upgraded, 3 newly installed, 0 to remove and 427 not upgraded.
250 not fully installed or removed.
Need to get 0 B/69.5 MB of archives.
After this operation, 85.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-headless_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb (--unpack):
 openjdk-6-jre-headless: 6b24-1.11.3-1ubuntu0.12.04.1 (Multi-Arch: same) is not co-installable with openjdk-6-jre-headless:i386 6b24-1.11.3-1ubuntu0.11.10.1 (Multi-Arch: no) which is currently installed
dpkg: error processing /var/cache/apt/archives/icedtea-6-jre-cacao_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb (--unpack):
 icedtea-6-jre-cacao: 6b24-1.11.3-1ubuntu0.12.04.1 (Multi-Arch: same) is not co-installable with icedtea-6-jre-cacao:i386 6b24-1.11.3-1ubuntu0.11.10.1 (Multi-Arch: no) which is currently installed
dpkg: error processing /var/cache/apt/archives/icedtea-6-jre-jamvm_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb (--unpack):
 icedtea-6-jre-jamvm: 6b24-1.11.3-1ubuntu0.12.04.1 (Multi-Arch: same) is not co-installable with icedtea-6-jre-jamvm:i386 6b24-1.11.3-1ubuntu0.11.10.1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-headless_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb
 /var/cache/apt/archives/icedtea-6-jre-cacao_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb
 /var/cache/apt/archives/icedtea-6-jre-jamvm_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
raihan@raihan-desktop:~$ penjdk-6-jre-headless

```

also facing crash problem . This Massage showing
```

we are sorry ,kde acivity Manageeer closed unexpectedly.

Executable: kactivitymanagerd PID: 1315 Signal: Segmentation fault (11)

```

please help solve all this problem .

---

### Post by oldos2er on 2012-08-27
Can you run this command, and if there are errors post them here? ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Raihan004 on 2012-08-27
> **oldos2er said:**
> Can you run this command, and if there are errors post them here? ```
sudo apt-get update && sudo apt-get upgrade
```

bro this will solve my all problem ?
can i install anything?like media coddec and usefull soft?
and also it solve my crashing problem ?
thank for your rappid ans my question .

after run those code this are happen
```


raihan@raihan-desktop:~$ sudo codeblock
[sudo] password for raihan: 
sudo: codeblock: command not found
raihan@raihan-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Ign http://bd.archive.ubuntu.com precise InRelease                                                                           
Ign http://bd.archive.ubuntu.com precise-updates InRelease          
Ign http://bd.archive.ubuntu.com precise-backports InRelease
Ign http://security.ubuntu.com precise-security InRelease
Ign http://extras.ubuntu.com precise InRelease                       
Hit http://bd.archive.ubuntu.com precise Release.gpg                 
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://bd.archive.ubuntu.com precise-updates Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://extras.ubuntu.com precise Release                          
Get:1 http://bd.archive.ubuntu.com precise-backports Release.gpg [198 B]
Hit http://bd.archive.ubuntu.com precise Release                     
Hit http://extras.ubuntu.com precise/main Sources                                           
Hit http://security.ubuntu.com precise-security/main Sources         
Hit http://bd.archive.ubuntu.com precise-updates Release
Get:2 http://bd.archive.ubuntu.com precise-backports Release [49.6 kB]                      
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                                     
Hit http://security.ubuntu.com precise-security/restricted Sources                                                           
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                      
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                   
Hit http://security.ubuntu.com precise-security/universe Sources                                                             
Hit http://security.ubuntu.com precise-security/multiverse Sources                                                           
Hit http://security.ubuntu.com precise-security/main amd64 Packages                                                          
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                                                    
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                                                      
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                                                    
Hit http://security.ubuntu.com precise-security/main i386 Packages                                                           
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                                                     
Hit http://security.ubuntu.com precise-security/universe i386 Packages                                                       
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                                                     
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                        
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                  
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                  
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                    
Hit http://bd.archive.ubuntu.com precise/main Sources                                                                        
Hit http://bd.archive.ubuntu.com precise/restricted Sources                                                                  
Hit http://bd.archive.ubuntu.com precise/universe Sources                                                                    
Hit http://bd.archive.ubuntu.com precise/multiverse Sources                                                                  
Hit http://bd.archive.ubuntu.com precise/main amd64 Packages                                                                 
Hit http://bd.archive.ubuntu.com precise/restricted amd64 Packages                                                           
Hit http://bd.archive.ubuntu.com precise/universe amd64 Packages                                                             
Hit http://bd.archive.ubuntu.com precise/multiverse amd64 Packages                                                           
Hit http://bd.archive.ubuntu.com precise/main i386 Packages                                                                  
Hit http://bd.archive.ubuntu.com precise/restricted i386 Packages                                                            
Hit http://bd.archive.ubuntu.com precise/universe i386 Packages                                                              
Hit http://bd.archive.ubuntu.com precise/multiverse i386 Packages                                                            
Hit http://bd.archive.ubuntu.com precise/main TranslationIndex                                                               
Hit http://bd.archive.ubuntu.com precise/multiverse TranslationIndex                                                         
Hit http://bd.archive.ubuntu.com precise/restricted TranslationIndex                                                         
Hit http://bd.archive.ubuntu.com precise/universe TranslationIndex                                                           
Hit http://bd.archive.ubuntu.com precise-updates/main Sources                                                                
Hit http://bd.archive.ubuntu.com precise-updates/restricted Sources                                                          
Hit http://bd.archive.ubuntu.com precise-updates/universe Sources                                                            
Hit http://bd.archive.ubuntu.com precise-updates/multiverse Sources                                                          
Hit http://bd.archive.ubuntu.com precise-updates/main amd64 Packages                                                         
Hit http://bd.archive.ubuntu.com precise-updates/restricted amd64 Packages                                                   
Hit http://bd.archive.ubuntu.com precise-updates/universe amd64 Packages                                                     
Hit http://bd.archive.ubuntu.com precise-updates/multiverse amd64 Packages                                                   
Hit http://bd.archive.ubuntu.com precise-updates/main i386 Packages                                                          
Hit http://bd.archive.ubuntu.com precise-updates/restricted i386 Packages                                                    
Hit http://bd.archive.ubuntu.com precise-updates/universe i386 Packages                                                      
Hit http://bd.archive.ubuntu.com precise-updates/multiverse i386 Packages                                                    
Hit http://bd.archive.ubuntu.com precise-updates/main TranslationIndex                                                       
Hit http://bd.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                 
Hit http://bd.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                 
Hit http://bd.archive.ubuntu.com precise-updates/universe TranslationIndex                                                   
Get:3 http://bd.archive.ubuntu.com precise-backports/main Sources [2,422 B]                                                  
Get:4 http://bd.archive.ubuntu.com precise-backports/restricted Sources [14 B]                                               
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                  
Get:5 http://bd.archive.ubuntu.com precise-backports/universe Sources [13.5 kB]                                              
Ign http://extras.ubuntu.com precise/main Translation-en                                                                     
Get:6 http://bd.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]                                            
Get:7 http://bd.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]                                           
Get:8 http://bd.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                                        
Get:9 http://bd.archive.ubuntu.com precise-backports/universe amd64 Packages [11.9 kB]                                       
Get:10 http://bd.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]                                      
Get:11 http://bd.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]                                           
Get:12 http://bd.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                        
Get:13 http://bd.archive.ubuntu.com precise-backports/universe i386 Packages [12.0 kB]                                       
Hit http://security.ubuntu.com precise-security/main Translation-en                                                          
Get:14 http://bd.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]                                       
Hit http://bd.archive.ubuntu.com precise-backports/main TranslationIndex                                                     
Hit http://bd.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                               
Hit http://bd.archive.ubuntu.com precise-backports/restricted TranslationIndex                                               
Hit http://bd.archive.ubuntu.com precise-backports/universe TranslationIndex                                                 
Hit http://bd.archive.ubuntu.com precise/main Translation-en                                                                 
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                    
Hit http://bd.archive.ubuntu.com precise/multiverse Translation-en                                                           
Hit http://bd.archive.ubuntu.com precise/restricted Translation-en                                                           
Hit http://bd.archive.ubuntu.com precise/universe Translation-en                                                             
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                    
Hit http://bd.archive.ubuntu.com precise-updates/main Translation-en                                                         
Hit http://bd.archive.ubuntu.com precise-updates/multiverse Translation-en                                                   
Hit http://bd.archive.ubuntu.com precise-updates/restricted Translation-en                                                   
Hit http://bd.archive.ubuntu.com precise-updates/universe Translation-en                                                     
Hit http://bd.archive.ubuntu.com precise-backports/main Translation-en                                                       
Hit http://bd.archive.ubuntu.com precise-backports/multiverse Translation-en                                                 
Hit http://bd.archive.ubuntu.com precise-backports/restricted Translation-en                                                 
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                      
Hit http://bd.archive.ubuntu.com precise-backports/universe Translation-en                                                   
Fetched 96.9 kB in 1min 6s (1,464 B/s)                                                                                       
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ca-certificates-java : Depends: openjdk-6-jre-headless (>= 6b16-1.6.1-2) but it is not installed or
                                 java6-runtime-headless
 gbrainy : Depends: liblaunchpad-integration1.0-cil (>= 0.1.33) but it is not installed
 libavcodec-extra-53:i386 : Depends: libavutil-extra-51:i386 (< 4:0.7.6ubuntu0.11.10.1+medibuntu1-99) but 4:0.8.3ubuntu0.12.04.1 is installed
                            Depends: libfaac0:i386 but it is not installed
                            Depends: libopencore-amrnb0:i386 but it is not installed
                            Depends: libopencore-amrwb0:i386 but it is not installed
                            Depends: libvpx0:i386 (>= 0.9.0) but it is not installable
                            Depends: libx264-116:i386 but it is not installable
                            Recommends: apport-hooks-medibuntu:i386 but it is not installable
 libavdevice53:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not installed or
                               libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is installed
 libavfilter2:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not installed or
                              libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is installed
                     Depends: libswscale2:i386 (< 4:0.7.6-99) but it is not installed or
                              libswscale-extra-2:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is installed
 libavformat53:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not installed or
                               libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is installed
 openjdk-6-jre-headless:i386 : Depends: openjdk-6-jre-lib:i386 (>= 6b24-1.11.3-1ubuntu0.11.10.1)
                               Depends: ca-certificates-java:i386
                               Depends: libjpeg62:i386 but it is not installed
 openjdk-6-jre-lib : Depends: openjdk-6-jre-headless (>= 6b17) but it is not installed
 telepathy-idle:i386 : Depends: libssl1.0.0:i386 (>= 1.0.0) but it is not installed
 telepathy-logger:i386 : Depends: libtelepathy-logger2:i386 (= 0.2.10-2) but 0.4.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
raihan@raihan-desktop:~$ 

```
what i do now?

---

### Post by oldos2er on 2012-08-27
I was hoping "sudo apt-get update" would solve your dependency problems. One more thing to try would be to change to using the main server instead of the Bangladeshi one. Run ```
kdesudo software-properties-kde
``` and choose 'Main server' from the Download from: drop-down menu. After you've done that, try the command again. ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by drmrgd on 2012-08-27
Deleted

---

### Post by Raihan004 on 2012-08-27
> **oldos2er said:**
> I was hoping "sudo apt-get update" would solve your dependency problems. One more thing to try would be to change to using the main server instead of the Bangladeshi one. Run ```
gksu software-properties-gtk
``` and choose 'Main server' from the Download from: drop-down menu. After you've done that, try the command again. ```
sudo apt-get update && sudo apt-get upgrade
```

not work
```
raihan@raihan-desktop:~$ gksu software-properties-gtk
The program 'gksu' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
raihan@raihan-desktop:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ca-certificates-java : Depends: openjdk-6-jre-headless (>= 6b16-1.6.1-2) but it is not going to be installed or
                                 java6-runtime-headless
 gbrainy : Depends: liblaunchpad-integration1.0-cil (>= 0.1.33) but it is not going to be installed
 gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
        Recommends: gnome-keyring but it is not going to be installed
 libavcodec-extra-53:i386 : Depends: libavutil-extra-51:i386 (< 4:0.7.6ubuntu0.11.10.1+medibuntu1-99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                            Depends: libfaac0:i386 but it is not going to be installed
                            Depends: libopencore-amrnb0:i386 but it is not going to be installed
                            Depends: libopencore-amrwb0:i386 but it is not going to be installed
                            Depends: libvpx0:i386 (>= 0.9.0) but it is not installable
                            Depends: libx264-116:i386 but it is not installable
                            Recommends: apport-hooks-medibuntu:i386 but it is not installable
 libavdevice53:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not going to be installed or
                               libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
 libavfilter2:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not going to be installed or
                              libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
                     Depends: libswscale2:i386 (< 4:0.7.6-99) but it is not going to be installed or
                              libswscale-extra-2:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
 libavformat53:i386 : Depends: libavutil51:i386 (< 4:0.7.6-99) but it is not going to be installed or
                               libavutil-extra-51:i386 (< 4:0.7.6.99) but 4:0.8.3ubuntu0.12.04.1 is to be installed
 openjdk-6-jre-headless:i386 : Depends: openjdk-6-jre-lib:i386 (>= 6b24-1.11.3-1ubuntu0.11.10.1)
                               Depends: ca-certificates-java:i386
                               Depends: libjpeg62:i386 but it is not going to be installed
 openjdk-6-jre-lib : Depends: openjdk-6-jre-headless (>= 6b17) but it is not going to be installed
 telepathy-idle:i386 : Depends: libssl1.0.0:i386 (>= 1.0.0) but it is not going to be installed
 telepathy-logger:i386 : Depends: libtelepathy-logger2:i386 (= 0.2.10-2) but 0.4.0-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by oldos2er on 2012-08-27
Sorry, try using "gksudo" instead. But it seems odd that 'gksu' is not there, I thought it was installed by default.

---

### Post by Raihan004 on 2012-08-27
> **oldos2er said:**
> Sorry, try using "gksudo" instead. But it seems odd that 'gksu' is not there, I thought it was installed by default.

not work
```
raihan@raihan-desktop:~$ gksudo software-properties-gtk

(gksudo:8059): GLib-GIO-ERROR **: Settings schema 'org.gnome.desktop.interface' is not installed

Trace/breakpoint trap

```

if i wana install anything always facing this problem 
```
Package: /var/cache/apt/archives/openjdk-6-jre-headless_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb
Error: openjdk-6-jre-headless: 6b24-1.11.3-1ubuntu0.12.04.1 (Multi-Arch

Package: /var/cache/apt/archives/icedtea-6-jre-cacao_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb
Error: icedtea-6-jre-cacao: 6b24-1.11.3-1ubuntu0.12.04.1 (Multi-Arch

Package: /var/cache/apt/archives/icedtea-6-jre-jamvm_6b24-1.11.3-1ubuntu0.12.04.1_amd64.deb
Error: icedtea-6-jre-jamvm: 6b24-1.11.3-1ubuntu0.12.04.1 (Multi-Arc
```

---

### Post by oldos2er on 2012-08-28
Try clearing the cache: ```
sudo apt-get clean
```

Edit: I'm an idiot. Of course with Kubuntu you'll be using "kdesudo" instead of "gksu" or "gksudo". Sorry about that. I've edited the command I gave you in post #4. You could also use Muon  to change servers, under Settings, Software Sources.

---

