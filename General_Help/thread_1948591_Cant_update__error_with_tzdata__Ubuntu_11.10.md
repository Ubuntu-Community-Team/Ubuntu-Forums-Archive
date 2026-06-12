---
title: "Cant update:  error with tzdata  Ubuntu 11.10"
date: 2012-03-28
forum: General Help
---

### Post by majordread on 2012-03-28
I am still relatively new with Ubuntu, and have been learning, but recently I have been at a loss of finding a solution on my own with the errors I am receiving. I cannot update through a terminal nor with the update manager. When I run a 

sudo apt-get update    I get this:

```
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get update
[sudo] password for tyler: 
Ign http://dl.google.com stable InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://packages.medibuntu.org oneiric InRelease                            
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://lgp203.free.fr oneiric InRelease                                    
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Get:2 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://extras.ubuntu.com oneiric Release                                   
Ign http://ppa.launchpad.net maverick InRelease                                
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://archive.getdeb.net oneiric-getdeb InRelease                         
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://packages.medibuntu.org oneiric/free amd64 Packages                  
Hit http://archive.canonical.com oneiric Release                               
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://us.archive.ubuntu.com oneiric Release                               
Hit http://lgp203.free.fr oneiric Release.gpg                                  
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://packages.medibuntu.org oneiric/non-free amd64 Packages              
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:3 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://lgp203.free.fr oneiric Release                                      
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.getdeb.net oneiric-getdeb Release.gpg                       
Hit http://lgp203.free.fr oneiric/universe Sources                             
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://lgp203.free.fr oneiric/unstable Sources                             
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:4 http://us.archive.ubuntu.com oneiric-updates/main Sources [132 kB]       
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main TranslationIndex                    
Hit http://lgp203.free.fr oneiric/universe amd64 Packages                      
Hit http://archive.getdeb.net oneiric-getdeb Release                           
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Get:5 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:6 http://us.archive.ubuntu.com oneiric-updates/universe Sources [48.8 kB]  
Hit http://lgp203.free.fr oneiric/unstable amd64 Packages                      
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Get:7 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,661 B]
Get:8 http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages [307 kB]
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en                
Hit http://lgp203.free.fr oneiric/universe i386 Packages                       
Hit http://archive.getdeb.net oneiric-getdeb/games amd64 Packages              
Get:9 http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:10 http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages [104 kB]
Hit http://lgp203.free.fr oneiric/unstable i386 Packages                       
Get:11 http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,210 B]
Get:12 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [307 kB]
Ign http://lgp203.free.fr oneiric/universe TranslationIndex                    
Hit http://archive.getdeb.net oneiric-getdeb/games i386 Packages               
Ign http://archive.getdeb.net oneiric-getdeb/games TranslationIndex            
Get:13 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:14 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [104 kB]
Ign http://lgp203.free.fr oneiric/unstable TranslationIndex                    
Get:15 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,356 B]
Get:16 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:17 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:18 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:19 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages   
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages          
Err http://ppa.launchpad.net oneiric/main amd64 Packages                       
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net maverick/main Translation-en_US                   
Ign http://ppa.launchpad.net maverick/main Translation-en                      
Ign http://packages.medibuntu.org oneiric/free Translation-en_US               
Ign http://packages.medibuntu.org oneiric/free Translation-en                  
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_US           
Ign http://packages.medibuntu.org oneiric/non-free Translation-en              
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en_US           
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en              
Ign http://lgp203.free.fr oneiric/universe Translation-en_US                   
Ign http://lgp203.free.fr oneiric/universe Translation-en               
Ign http://lgp203.free.fr oneiric/unstable Translation-en_US            
Ign http://lgp203.free.fr oneiric/unstable Translation-en
Get:20 http://dl.google.com stable Release [1,338 B]
Get:21 http://dl.google.com stable/main amd64 Packages [469 B]
Get:22 http://dl.google.com stable/main i386 Packages [464 B]                  
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en
Fetched 1,071 kB in 3min 28s (5,127 B/s)
W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. 
```and when I run a sudo apt-get dist-upgrade I get this:

```
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get dist-upgrade
[sudo] password for tyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.0.0-17 linux-headers-3.0.0-17-generic
  linux-image-3.0.0-17-generic
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin app-install-data-partner apt
  apt-transport-https apt-utils ca-certificates-java checkbox checkbox-gtk
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg deluge
  deluge-common deluge-gtk firefox firefox-globalmenu firefox-gnome-support
  firefox-locale-en gstreamer0.10-gconf gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio jupiter language-pack-en language-pack-gnome-en
  libafpclient0 libapt-inst1.3 libapt-pkg4.11 libc-bin libc-dev-bin libc6
  libc6:i386 libc6-dev libc6-i386 libcec libfreetype6 libfreetype6:i386
  libgudev-1.0-0 liblightdm-gobject-1-0 libmysqlclient16
  libnautilus-extension1 libnfs0 libpng12-0 libpng12-0:i386 librtmp0
  librtmp0:i386 libudev0 lightdm linux-generic linux-headers-3.0.0-16
  linux-headers-3.0.0-16-generic linux-headers-generic
  linux-image-3.0.0-16-generic linux-image-generic linux-libc-dev
  multiarch-support mysql-common nautilus nautilus-data python-pam
  software-center thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us udev
  xbmc xbmc-bin xserver-xorg-video-openchrome xul-ext-ubufox
72 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/235 MB of archives.
After this operation, 257 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up tzdata (2012b-0ubuntu0.11.10) ...
/var/lib/dpkg/info/tzdata.config: 348: head: not found
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Any help would be very much appreciated, as there are many updates that could really help my system out. Thanks.

---

### Post by raja.genupula on 2012-03-28
do this in terminal```

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install -f
```

let us know what you got

---

### Post by majordread on 2012-03-28
sudo apt-get autoremove gives me this

```
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get autoremove
[sudo] password for tyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms frei0r-plugins libasound2:i386 libasound2-plugins:i386 libasyncns0:i386
  libatk1.0-0:i386 libcairo2:i386 libcv2.1 libcvaux2.1 libdatrie1:i386
  libenet1a libflac8:i386 libftdi1 libgavl1 libgdk-pixbuf2.0-0:i386
  libgoocanvas-common libgoocanvas3 libgtk2.0-0:i386 libhighgui2.1
  libirrlicht1.7a libjack-jackd2-0:i386 libjasper1:i386 libjson0:i386
  libmlt-data libnspr4-0d:i386 libnss3-1d:i386 libogg0:i386 libpango1.0-0:i386
  libpixman-1-0:i386 libpulse0:i386 libsamplerate0:i386 libsndfile1:i386
  libsox-fmt-alsa libsox-fmt-base libsox1b libspeexdsp1:i386 libthai0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386 libxft2:i386
  libxinerama1:i386 libxrandr2:i386 nspluginviewer:i386 nvidia-settings
  nvidia-settings-updates openshot-doc python-pygoocanvas
  screen-resolution-extra setserial
0 upgraded, 0 newly installed, 54 to remove and 72 not upgraded.
2 not fully installed or removed.
After this operation, 63.8 MB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up tzdata (2012b-0ubuntu0.11.10) ...
/var/lib/dpkg/info/tzdata.config: 348: head: not found
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by raja.genupula on 2012-03-28
[http://pastebin.com/2A8he4rW](http://pastebin.com/2A8he4rW)

that link have my tzdata file , so now do as

```
sudo nautilus
```

then from the filesystem navigate to /var/lib/dpkg/info this location and replace the  total code of tzdata.config with information we had in that pastebin link . 

try again .all the best .

---

### Post by majordread on 2012-03-28
Thanks for the fast replies by the way. I did as you said and replaced the text of the tzdata.config and still get the same errors.

---

### Post by cortman on 2012-03-28
Hi,

Please post the output of

```
cat /var/lib/dpkg/info/tzdata.config
```

---

### Post by majordread on 2012-03-28
This is it:

```
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ cat /var/lib/dpkg/info/tzdata.config
#! /bin/sh
set -e

. /usr/share/debconf/confmodule
db_version 2.0
db_capb backup

convert_timezone()
{
    case "$1" in
    (right/*|posix/*)
        convert_timezone "${1#*/}"
        ;;
    ("Africa/Asmera")
        echo "Africa/Asmara"
        ;;
    ("America/Argentina/ComodRivadavia"|"America/Catamarca")
        echo "America/Argentina/Catamarca"
        ;;
    ("America/Buenos_Aires")
        echo "America/Argentina/Buenos_Aires"
        ;;
    ("America/Cordoba"|"America/Rosario")
        echo "America/Argentina/Cordoba"
        ;;
    ("America/Jujuy")
        echo "America/Argentina/Jujuy"
        ;;
    ("America/Mendoza")
        echo "America/Argentina/Mendoza"
        ;;
    ("Antarctica/South_Pole")
        echo "Antarctica/McMurdo"
        ;;
        "Asia/Ashkhabad")
            echo "Asia/Ashgabat"
            ;;
        ("Asia/Calcutta")
            echo "Asia/Kolkata"
            ;;
        "Asia/Chungking")
            echo "Asia/Chongqing"
            ;;
        "Asia/Dacca")
            echo "Asia/Dhaka"
            ;;
        ("Asia/Katmandu")
            echo "Asia/Kathmandu"
            ;;
        "Asia/Macao")
            echo "Asia/Macau"
            ;;
        ("Asia/Saigon")
            echo "Asia/Ho_Chi_Minh"
            ;;
        "Asia/Thimbu")
            echo "Asia/Thimphu"
            ;;
        "Asia/Ulan_Bator")
            echo "Asia/Ulaanbaatar"
            ;;
        "Atlantic/Faeroe")
            echo "Atlantic/Faroe"
            ;;
        "Australia/ACT" | "Australia/NSW")
            echo "Australia/Sydney"
            ;;
        "Australia/LHI")
            echo "Australia/Lord_Howe"
            ;;
        "Australia/North")
            echo "Australia/Darwin"
            ;;
        "Australia/Queensland")
            echo "Australia/Brisbane"
            ;;
        "Australia/South")
            echo "Australia/Adelaide"
            ;;
        "Australia/Tasmania")
            echo "Australia/Hobart"
            ;;
        "Australia/Victoria")
            echo "Australia/Melbourne"
            ;;
        "Australia/West")
            echo "Australia/Perth"
            ;;
        "Brazil/Acre")
            echo "America/Rio_Branco"
            ;;
        "Brazil/DeNoronha")
            echo "America/Noronha"
            ;;
        "Brazil/East")
            echo "America/Sao_Paulo"
            ;;
        "Brazil/West")
            echo "America/Manaus"
            ;;
        "Canada/Atlantic")
            echo "America/Halifax"
            ;;
        "Canada/Central")
            echo "America/Winnipeg"
            ;;
        "Canada/East-Saskatchewan")
            echo "America/Regina"
            ;;
        "Canada/Eastern")
            echo "America/Toronto"
            ;;
        "Canada/Mountain")
            echo "America/Edmonton"
            ;;
        "Canada/Newfoundland")
            echo "America/St_Johns"
            ;;
        "Canada/Pacific")
            echo "America/Vancouver"
            ;;
        "Canada/Saskatchewan")
            echo "America/Regina"
            ;;
        "Canada/Yukon")
            echo "America/Whitehorse"
            ;;
        "CET")
            echo "Europe/Paris"
            ;;
        "Chile/Continental")
            echo "America/Santiago"
            ;;
        "Chile/EasterIsland")
            echo "Pacific/Easter"
            ;;
        "CST6CDT")
            echo "SystemV/CST6CDT"
            ;;
        "Cuba")
            echo "America/Havana"
            ;;
        "EET")
            echo "Europe/Helsinki"
            ;;
        "Egypt")
            echo "Africa/Cairo"
            ;;
        "Eire")
            echo "Europe/Dublin"
            ;;
        "EST")
            echo "SystemV/EST5"
            ;;
        "EST5EDT")
            echo "SystemV/EST5EDT"
            ;;
        "GB")
            echo "Europe/London"
            ;;
        "GB-Eire")
            echo "Europe/London"
            ;;
        "GMT")
            echo "Etc/GMT"
            ;;
        "GMT0")
            echo "Etc/GMT0"
            ;;
        "GMT-0")
            echo "Etc/GMT-0"
            ;;
        "GMT+0")
            echo "Etc/GMT+0"
            ;;
        "Greenwich")
            echo "Etc/Greenwich"
            ;;
        "Hongkong")
            echo "Asia/Hong_Kong"
            ;;
        "HST")
            echo "Pacific/Honolulu"
            ;;
        "Iceland")
            echo "Atlantic/Reykjavik"
            ;;
        "Iran")
            echo "Asia/Tehran"
            ;;
        "Israel")
            echo "Asia/Tel_Aviv"
            ;;
        "Jamaica")
            echo "America/Jamaica"
            ;;
        "Japan")
            echo "Asia/Tokyo"
            ;;
        "Kwajalein")
            echo "Pacific/Kwajalein"
            ;;
        "Libya")
            echo "Africa/Tripoli"
            ;;
        "MET")
            echo "Europe/Paris"
            ;;
        "Mexico/BajaNorte")
            echo "America/Tijuana"
            ;;
        "Mexico/BajaSur")
            echo "America/Mazatlan"
            ;;
        "Mexico/General")
            echo "America/Mexico_City"
            ;;
        "Mideast/Riyadh87")
            echo "Asia/Riyadh87"
            ;;
        "Mideast/Riyadh88")
            echo "Asia/Riyadh88"
            ;;
        "Mideast/Riyadh89")
            echo "Asia/Riyadh89"
            ;;
        "MST")
            echo "SystemV/MST7"
            ;;
        "MST7MDT")
            echo "SystemV/MST7MDT"
            ;;
        "Navajo")
            echo "America/Denver"
            ;;
        "NZ")
            echo "Pacific/Auckland"
            ;;
        "NZ-CHAT")
            echo "Pacific/Chatham"
            ;;
        "Poland")
            echo "Europe/Warsaw"
            ;;
        "Portugal")
            echo "Europe/Lisbon"
            ;;
        "PRC")
            echo "Asia/Shanghai"
            ;;
        "PST8PDT")
            echo "SystemV/PST8PDT"
            ;;
        "ROC")
            echo "Asia/Taipei"
            ;;
        "ROK")
            echo "Asia/Seoul"
            ;;
        "Singapore")
            echo "Asia/Singapore"
            ;;
        "Turkey")
            echo "Europe/Istanbul"
            ;;
        "UCT")
            echo "Etc/UCT"
            ;;
        "Universal")
            echo "Etc/UTC"
            ;;
        "US/Alaska")
            echo "America/Anchorage"
            ;;
        "US/Aleutian")
            echo "America/Adak"
            ;;
        "US/Arizona")
            echo "America/Phoenix"
            ;;
        "US/Central")
            echo "America/Chicago"
            ;;
        "US/East-Indiana")
            echo "America/Indianapolis"
            ;;
        "US/Eastern")
            echo "America/New_York"
            ;;
        "US/Hawaii")
            echo "Pacific/Honolulu"
            ;;
        "US/Indiana-Starke")
            echo "America/Indianapolis"
            ;;
        "US/Michigan")
            echo "America/Detroit"
            ;;
        "US/Mountain")
            echo "America/Denver"
            ;;
        "US/Pacific")
            echo "America/Los_Angeles"
            ;;
        "US/Samoa")
            echo "Pacific/Pago_Pago"
            ;;
        "UTC")
            echo "Etc/UTC"
            ;;
        "WET")
            echo "Europe/Lisbon"
            ;;
        "W-SU")
            echo "Europe/Moscow"
            ;;
        "Zulu")
            echo "Etc/UTC"
            ;;
        *)
            echo "$1"
            ;;
    esac
}

# If /etc/localtime is a link, update /etc/timezone
if [ -L /etc/localtime ] ; then
    TIMEZONE="$(readlink /etc/localtime)"
    TIMEZONE="${TIMEZONE#/usr/share/zoneinfo/}"
    if [ -f "/usr/share/zoneinfo/$TIMEZONE" ] ; then
        echo ${TIMEZONE} > /etc/timezone
    fi
fi

# Read /etc/timezone
if [ -e /etc/timezone ]; then
    TIMEZONE="$(head -n 1 /etc/timezone)"
    TIMEZONE="${TIMEZONE%% *}"
    TIMEZONE="${TIMEZONE##/}"
    TIMEZONE="${TIMEZONE%%/}"
    TIMEZONE="$(convert_timezone $TIMEZONE)"
    if [ -f "/usr/share/zoneinfo/$TIMEZONE" ] ; then
        AREA="${TIMEZONE%%/*}"
        ZONE="${TIMEZONE#*/}"
    else
        rm -f /etc/timezone
    fi
fi

# The timezone is already configured
if [ -e /etc/timezone ] && [ -e /etc/localtime ] ; then
    # Don't ask the user, except if he/she explicitely asked that
    if [ -z "$DEBCONF_RECONFIGURE" ] ; then
        db_fset tzdata/Areas seen true
        db_fset tzdata/Zones/$AREA seen true
    fi
# The timezone has never been configured or is falsely configured
elif ! [ -e /etc/localtime ] || [ -n "$DEBCONF_RECONFIGURE" ] ; then
    if [ -z "$AREA" ] || [ -z "$ZONE" ] ; then
        RET=""
        db_get tzdata/Areas || true
        if [ -n "$RET" ] ; then
            AREA=$RET
        else
            AREA="Etc"
        fi

        RET=""
        db_get tzdata/Zones/$AREA || RET=true
        if [ -n "$RET" ] ; then
            ZONE=$RET
        else
            ZONE="UTC"
        fi

        echo "$AREA/$ZONE" > /etc/timezone
    fi
    db_fset tzdata/Areas seen false
    db_fset tzdata/Zones/$AREA seen false
# The user want to handle the timezone by him/herself
else
    exit 0
fi

# Initializes debconf default values from the ones found in
# configuration files
db_set tzdata/Areas "$AREA"
db_set tzdata/Zones/$AREA "$ZONE"

STATE=1
while [ "$STATE" -ge 0 ]; do
    case "$STATE" in
    0)
        # The user has cancel the timezone change, reset the debconf
        # values to the initial one.
        db_set tzdata/Areas "$AREA"
        db_set tzdata/Zones/$AREA "$ZONE"
        break
        ;;
    1)
        # Ask the user of the Area
        db_input high tzdata/Areas || true
        ;;
    2)
        # Ask the user of the Zone
        db_get tzdata/Areas || RET=Etc
        db_input high tzdata/Zones/$RET || true
        ;;
    *)
        break
        ;;
    esac
    if db_go; then
        STATE=$(($STATE + 1))
    else
        STATE=$(($STATE - 1))
    fi
done




exit 0

```

---

### Post by cortman on 2012-03-28
Hm… grasping at straws here, but try renaming tzdata.config to tzdata.config.old. Make a new file called tzdata.config, and paste in Raja’s pastebin stuff. Then run

```
sudo apt-get install -f
```

---

### Post by majordread on 2012-03-28
No dice, still the same error.

---

### Post by majordread on 2012-03-28
After restarting, this is the new error I got:

```
sudotyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get dist-upgrade
[sudo] password for tyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.0.0-17 linux-headers-3.0.0-17-generic
  linux-image-3.0.0-17-generic
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin app-install-data-partner apt
  apt-transport-https apt-utils ca-certificates-java checkbox checkbox-gtk
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg deluge
  deluge-common deluge-gtk firefox firefox-globalmenu firefox-gnome-support
  firefox-locale-en gstreamer0.10-gconf gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio jupiter language-pack-en language-pack-gnome-en
  libafpclient0 libapt-inst1.3 libapt-pkg4.11 libc-bin libc-dev-bin libc6
  libc6:i386 libc6-dev libc6-i386 libcec libfreetype6 libfreetype6:i386
  libgudev-1.0-0 liblightdm-gobject-1-0 libmysqlclient16
  libnautilus-extension1 libnfs0 libpng12-0 libpng12-0:i386 librtmp0
  librtmp0:i386 libudev0 lightdm linux-generic linux-headers-3.0.0-16
  linux-headers-3.0.0-16-generic linux-headers-generic
  linux-image-3.0.0-16-generic linux-image-generic linux-libc-dev
  multiarch-support mysql-common nautilus nautilus-data python-pam
  software-center thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us udev
  xbmc xbmc-bin xserver-xorg-video-openchrome xul-ext-ubufox
72 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/235 MB of archives.
After this operation, 257 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up tzdata (2012b-0ubuntu0.11.10) ...
Can't exec "/var/lib/dpkg/info/tzdata.config": Permission denied at /usr/share/perl/5.12/IPC/Open3.pm line 168.
open2: exec of /var/lib/dpkg/info/tzdata.config configure 2011n-0ubuntu0.11.10 failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cortman on 2012-03-28
Run
  
 ```
chmod +x /var/lib/dpkg/info/tzdata.config
```
  
 Then
  
 ```
sudo apt-get install –f
```

---

### Post by majordread on 2012-03-29
Did that, this is what I now am getting:

```
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ sudo chmod +x /var/lib/dpkg/info/tzdata.config
[sudo] password for tyler: 
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libirrlicht1.7a libxcomposite1:i386 libwrap0:i386
  libsamplerate0:i386 screen-resolution-extra libsox-fmt-base libftdi1
  python-pygoocanvas libsox-fmt-alsa libgoocanvas3 libcvaux2.1
  libjack-jackd2-0:i386 libnspr4-0d:i386 libcairo2:i386 libdatrie1:i386
  libjson0:i386 setserial libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386
  openshot-doc nvidia-settings-updates libhighgui2.1 libxinerama1:i386
  libgoocanvas-common nspluginviewer:i386 libxft2:i386 dkms libgavl1
  libspeexdsp1:i386 libthai0:i386 frei0r-plugins libasound2:i386 libflac8:i386
  libcv2.1 libvorbisenc2:i386 libasyncns0:i386 libjasper1:i386
  libpango1.0-0:i386 libpulse0:i386 libenet1a libxcb-render0:i386 libsox1b
  libvorbis0a:i386 libmlt-data libxcursor1:i386 libxcb-shm0:i386
  libxrandr2:i386 libnss3-1d:i386 libsndfile1:i386 libgtk2.0-0:i386
  nvidia-settings libasound2-plugins:i386 libogg0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up tzdata (2012b-0ubuntu0.11.10) ...
/var/lib/dpkg/info/tzdata.config: 348: head: not found
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2012b-0ubuntu0.11.10); however:
  Package tzdata is not configured yet.
dpkg: error processing tzdata-java (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 tzdata
 tzdata-java
E: Sub-process /usr/bin/dpkg returned an error code (1)
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ 

```

---

### Post by raja.genupula on 2012-03-29
Hey Thanks cortman for your eye on this thread . 

@OP , hey i got something for you 
[http://ubuntuforums.org/archive/index.php/t-1232143.html](http://ubuntuforums.org/archive/index.php/t-1232143.html)

in the above thread try the solutions suggested by 
gartss

---

### Post by majordread on 2012-03-29
Well I feel like I can solve the problem based off this thread and a couple others, however when I edited the status I (stupidly) forgot to backup the original and deleted the lines for both tzdata and tzdata-java. From what I have figured out I only should have deleted the lines for tzdata and not the tzdata-java. But now without the tzdata-java lines I can not reinstall the package from the software center nor can I reinstall the tzdata or repair it. I have tried everything else, including dpkg --configure -a along with apt-get -f install and the dependencies can not install at all because of the broken tzdata file. 

So with all of that, I am currently at a loss. I thought I was on a trail.

---

### Post by majordread on 2012-03-29
I tried a sudo apt-get --fix-missing install -f and this is what I got:

```
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get --fix-missing install -fReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libirrlicht1.7a libxcomposite1:i386 libwrap0:i386
  libsamplerate0:i386 screen-resolution-extra libsox-fmt-base libftdi1
  python-pygoocanvas libsox-fmt-alsa libgoocanvas3 libcvaux2.1
  libjack-jackd2-0:i386 libnspr4-0d:i386 libcairo2:i386 libdatrie1:i386
  libjson0:i386 setserial libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386
  openshot-doc nvidia-settings-updates libhighgui2.1 libxinerama1:i386
  libgoocanvas-common nspluginviewer:i386 libxft2:i386 dkms libgavl1
  libspeexdsp1:i386 libthai0:i386 frei0r-plugins libasound2:i386 libflac8:i386
  libcv2.1 libvorbisenc2:i386 libasyncns0:i386 libjasper1:i386
  libpango1.0-0:i386 libpulse0:i386 libenet1a libxcb-render0:i386 libsox1b
  libvorbis0a:i386 libmlt-data libxcursor1:i386 libxcb-shm0:i386
  libxrandr2:i386 libnss3-1d:i386 libsndfile1:i386 libgtk2.0-0:i386
  nvidia-settings libasound2-plugins:i386 libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tzdata-java
The following NEW packages will be installed:
  tzdata-java
0 upgraded, 1 newly installed, 0 to remove and 72 not upgraded.
1 not fully installed or removed.
Need to get 0 B/134 kB of archives.
After this operation, 1,991 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up tzdata (2012b-0ubuntu0.11.10) ...
/var/lib/dpkg/info/tzdata.config: 348: head: not found
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and then tried a sudo apt-get upgrade and got:

```
tyler@tyler-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 openjdk-6-jre-headless : Depends: tzdata-java but it is not installed
E: Unmet dependencies. Try using -f.
```

So I looked at the openjdk-6-jre-headless in synaptic and I cannot remove it or reinstall or repair it because of the error I have with tzdata. Everything that I can even come up with is not allowed because of the error with tzdata. No packages involving it can be edited and I can not update anything on my system.

---

### Post by raja.genupula on 2012-03-30
```
sudo rm /var/lib/dpkg/info/tzdata.config
sudo apt-get install --reinstall tzdata-java
```

then try again . 

all the best .

---

