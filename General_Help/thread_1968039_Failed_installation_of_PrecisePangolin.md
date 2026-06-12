---
title: "Failed installation of PrecisePangolin"
date: 2012-04-28
forum: General Help
---

### Post by stahan on 2012-04-28
Hey there,

just before my exams, i've decided to upgrade to 12.04. During the installation, i've been told that a number of packages were already installed. This left me with ubuntu missing the icons of dash home applications. Furthermore, when i try to type anything in firefox and/or LibreOffice, the program crashes. I've tried upgrade and update, but as you can see, not to great success. Any help would be highly appreciated.

Thanks
```

georgi@GolfDeltaZulu:~$ sudo apt-get update; sudo apt-get upgrade
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB           
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,470 B]          
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources [5,019 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources [155 kB]                                                                 
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]                                                              
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]                                                         
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB]                                                          
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB]                                                          
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [1,274 kB]                                                               
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]                                                          
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]                                                           
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                                                                      
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [5,093 B]                                                              
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [765 B]                                                          
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [1,032 B]                                                          
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [14 B]                                                           
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [19.0 kB]                                                       
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [757 B]                                                   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [2,083 B]                                                   
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [14 B]                                                    
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [20.3 kB]                                                        
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [770 B]                                                    
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [2,088 B]                                                    
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [14 B]                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex                                                              
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources [700 B]                                                              
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                                         
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources [14 B]                                                           
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources [14 B]                                                         
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages [559 B]                                                       
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]                                                  
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages [14 B]                                                    
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages [14 B]                                                  
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages [559 B]                                                        
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                                   
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages [14 B]                                                     
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages [14 B]                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex                                                            
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources [1,550 B]                                                             
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources [14 B]                                                          
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources [2,143 B]                                                         
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources [14 B]                                                          
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages [12.0 kB]                                                      
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages [14 B]                                                   
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages [2,552 B]                                                  
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages [14 B]                                                   
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [11.9 kB]                                                       
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages [14 B]                                                    
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [2,571 B]                                                   
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [14 B]                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_GB                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_GB                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en_GB                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_GB                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en                                                               
Fetched 18.8 MB in 38s (494 kB/s)                                                                                                    
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 gnome-sudoku : Depends: gnome-games-common (= 1:3.2.1-0ubuntu1) but it is not installable
 gnomine : Depends: gnome-games-common (= 1:3.2.1-0ubuntu1) but it is not installable
 gtkpod : Depends: libgdl-3-1 (>= 3.0.2) but it is not installable
 gwibber-service : Depends: gir1.2-indicate-0.6 (>= 0.5.90) but it is not installable
 libanjuta-3-0 : Depends: libgdl-3-1 (>= 3.0.2) but it is not installable
 libflac8:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not installed
 libgphoto2-2:i386 : Depends: adduser:i386
 libgtk2.0-0:i386 : Depends: libxcursor1:i386 (> 1.1.2) but it is not installed
                    Depends: libxrandr2:i386 (>= 2:1.2.99.3) but it is not installed
 libpulse0:i386 : Depends: libasyncns0:i386 (>= 0.3) but it is not installed
                  Depends: libjson0:i386 but it is not installed
                  Depends: libwrap0:i386 (>= 7.6-4~) but it is not installed
 libsdl1.2debian : Depends: libsdl1.2debian-alsa (= 1.2.14-6.1ubuntu4) but it is not installable or
                            libsdl1.2debian-all (= 1.2.14-6.1ubuntu4) but it is not installable or
                            libsdl1.2debian-esd (= 1.2.14-6.1ubuntu4) but it is not installable or
                            libsdl1.2debian-oss (= 1.2.14-6.1ubuntu4) but it is not installable or
                            libsdl1.2debian-nas (= 1.2.14-6.1ubuntu4) but it is not installable or
                            libsdl1.2debian-pulseaudio (= 1.2.14-6.1ubuntu4) but it is not installable
 libsndfile1:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not installed
 libvorbis0a:i386 : Depends: libogg0:i386 (>= 1.1.0) but it is not installed
 libvorbisfile3:i386 : Depends: libogg0:i386 (>= 1.1.0) but it is not installed
 software-center : Depends: python-gobject-cairo
                   Recommends: lzma
 ubuntu-desktop : Depends: libsdl1.2debian-pulseaudio but it is not installable
                  Recommends: banshee-extension-ubuntuonemusicstore but it is not installable
                  Recommends: firefox-gnome-support but it is not installed
                  Recommends: gnome-codec-install
                  Recommends: gnome-mahjongg but it is not installable
                  Recommends: libgail-3-common but it is not installable
                  Recommends: libreoffice-help-en-us but it is not installed
 usb-creator-gtk : Depends: gir1.2-unity-4.0 but it is not installable
E: Unmet dependencies. Try using -f.
georgi@GolfDeltaZulu:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libvorbisfile3:i386:
 libvorbisfile3:i386 depends on libogg0 (>= 1.1.0).
dpkg: error processing libvorbisfile3:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libflac8:i386:
 libflac8:i386 depends on libogg0 (>= 1.0rc3).
dpkg: error processing libflac8:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-0:i386:
 libgtk2.0-0:i386 depends on libxcursor1 (>> 1.1.2).
 libgtk2.0-0:i386 depends on libxrandr2 (>= 2:1.2.99.3).
dpkg: error processing libgtk2.0-0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines-pixbuf:i386:
 gtk2-engines-pixbuf:i386 depends on libgtk2.0-0 (= 2.24.10-0ubuntu6); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing gtk2-engines-pixbuf:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpulse0:i386:
 libpulse0:i386 depends on libasyncns0 (>= 0.3).
 libpulse0:i386 depends on libjson0.
 libpulse0:i386 depends on libwrap0 (>= 7.6-4~).
dpkg: error processing libpulse0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail18:i386:
 libgail18:i386 depends on libgtk2.0-0 (= 2.24.10-0ubuntu6); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing libgail18:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsndfile1:i386:
 libsndfile1:i386 depends on libflac8 (>= 1.2.1); however:
  Package libflac8:i386 is not configured yet.
 libsndfile1:i386 depends on libogg0 (>= 1.0rc3); however:
dpkg: error processing libsndfile1:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librsvg2-common:i386:
 librsvg2-common:i386 depends on libgtk2.0-0 (>= 2.21.5); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing librsvg2-common:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-common:i386:
 libgail-common:i386 depends on libgail18 (= 2.24.10-0ubuntu6); however:
  Package libgail18:i386 is not configured yet.
dpkg: error processing libgail-common:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcanberra0:i386:
 libcanberra0:i386 depends on libvorbisfile3 (>= 1.1.2); however:
  Package libvorbisfile3:i386 is not configured yet.
dpkg: error processing libcanberra0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcanberra-gtk0:i386:
 libcanberra-gtk0:i386 depends on libcanberra0 (>= 0.12); however:
  Package libcanberra0:i386 is not configured yet.
 libcanberra-gtk0:i386 depends on libgtk2.0-0 (>= 2.24.0); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing libcanberra-gtk0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libvorbis0a:i386:
 libvorbis0a:i386 depends on libogg0 (>= 1.1.0).
dpkg: error processing libvorbis0a:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgphoto2-2:i386:
 libgphoto2-2:i386 depends on adduser.
dpkg: error processing libgphoto2-2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines-murrine:i386:
 gtk2-engines-murrine:i386 depends on libgtk2.0-0 (>= 2.24.5-4); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing gtk2-engines-murrine:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpulse-mainloop-glib0:i386:
 libpulse-mainloop-glib0:i386 depends on libpulse0 (>= 1:1.1-0ubuntu15); however:
  Package libpulse0:i386 is not configured yet.
dpkg: error processing libpulse-mainloop-glib0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libasound2-plugins:i386:
 libasound2-plugins:i386 depends on libpulse0 (>= 1:0.99.1); however:
  Package libpulse0:i386 is not configured yet.
dpkg: error processing libasound2-plugins:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libvorbisenc2:i386:
 libvorbisenc2:i386 depends on libvorbis0a (= 1.3.2-1ubuntu3); however:
  Package libvorbis0a:i386 is not configured yet.
dpkg: error processing libvorbisenc2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpulsedsp:i386:
 libpulsedsp:i386 depends on libpulse0 (>= 1:1.1-0ubuntu15); however:
  Package libpulse0:i386 is not configured yet.
dpkg: error processing libpulsedsp:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libvorbisfile3:i386
 libflac8:i386
 libgtk2.0-0:i386
 gtk2-engines-pixbuf:i386
 libpulse0:i386
 libgail18:i386
 libsndfile1:i386
 librsvg2-common:i386
 libgail-common:i386
 libcanberra0:i386
 libcanberra-gtk0:i386
 libvorbis0a:i386
 libgphoto2-2:i386
 gtk2-engines-murrine:i386
 libpulse-mainloop-glib0:i386
 libasound2-plugins:i386
 libvorbisenc2:i386
 libpulsedsp:i386
[23:23:42] &#1046;&#1086;&#1088;&#1086;: georgi@GolfDeltaZulu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgconf-2-4:i386 libatk1.0-0:i386 libxcomposite1:i386 libgail18:i386 libgphoto2-port0:i386 libgudev-1.0-0:i386
  libcairo-gobject2:i386 libcap2:i386 libproxy1:i386 libdbus-glib-1-2:i386 libtdb1:i386 gvfs-libs:i386 libxslt1.1:i386 libgomp1:i386
  libibus-1.0-0:i386 libcairo2:i386 libcanberra0:i386 gtk2-engines-murrine:i386 libsoup-gnome2.4-1:i386 librsvg2-common:i386
  libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386 libxaw7:i386 libxinerama1:i386 libxft2:i386 libcroco3:i386 libpulse-mainloop-glib0:i386
  libxml2:i386 libxmu6:i386 libcanberra-gtk0:i386 libvorbisfile3:i386 libxpm4:i386 libusb-0.1-4:i386 libgail-common:i386
  liborc-0.4-0:i386 libgd2-xpm:i386 libjasper1:i386 libgstreamer-plugins-base0.10-0:i386 libgnome-keyring0:i386 libxtst6:i386
  gtk2-engines-pixbuf:i386 librsvg2-2:i386 libpango1.0-0:i386 libpulsedsp:i386 gvfs:i386 libxcb-render0:i386 libexif12:i386
  libglu1-mesa:i386 libgstreamer0.10-0:i386 libxcb-shm0:i386 libgtk2.0-0:i386 libltdl7:i386 libllvm2.9:i386 glib-networking:i386
  libsoup2.4-1:i386 libgphoto2-2:i386 python-debtagshw gir1.2-gudev-1.0 software-center-aptdaemon-plugins libxrandr2:i386
  libxcursor1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  activity-log-manager-common activity-log-manager-control-center adduser anjuta-common aptdaemon c2esp checkbox checkbox-gtk
  checkbox-qt cmap-adobe-japan2 fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-nanum fonts-thai-tlwg
  fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee
  fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foo2zjs gir1.2-dee-1.0
  gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 gir1.2-gudev-1.0 gir1.2-indicate-0.7 gir1.2-rb-3.0
  gir1.2-ubuntuoneui-3.0 gir1.2-unity-5.0 gnome-games-data gnome-sudoku gnomine gtkpod gtkpod-data gwibber gwibber-service
  landscape-client-ui-install libanjuta-3-0 libasyncns0:i386 libatk-adaptor-schemas libdiscid0 libdmapsharing-3.0-2
  libfreerdp-plugins-standard libfreerdp1 libgdl-3-2 libgdl-3-common libgtkpod1 libindicate5 libjson0:i386 libmusicbrainz3-6
  libogg0:i386 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libqt4-sql-sqlite librhythmbox-core5 libsdl1.2debian
  libssh-4 libubuntuoneui-3.0-1 libvncserver0 libwrap0:i386 libxcursor1:i386 libxrandr2:i386 mahjongg min12xxw pnm2ppa
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix ptouch-driver pxljr python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-aptdaemon.pkcompat python-debtagshw python-dirspec python-gi-cairo
  python-indicate python-mako python-markupsafe python-packagekit python-ubuntu-sso-client rastertosag-gdi remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone software-center-aptdaemon-plugins
  splix syslinux-legacy ttf-khmeros-core ttf-thai-tlwg ubuntu-desktop ubuntu-sso-client ubuntu-sso-client-gtk usb-creator-common
  usb-creator-gtk whoopsie xz-lzma
Suggested packages:
  anjuta bonnie++ bootchart bzr cvs ethtool flex fwts git-core nmap smartmontools sox stress faad mp3gain python-jppy
  gwibber-service-flickr gwibber-service-digg gwibber-service-statusnet gwibber-service-foursquare gwibber-service-friendfeed
  gwibber-service-pingfm gwibber-service-qaiku unity-lens-gwibber xfreerdp libqt4-dev libvncserver0-dbg gnome-games-extra-data
  psutils hannah-foo2zjs tk8.4 tix magicfilter apsfilter python-beaker python-mako-doc
Recommended packages:
  ecryptfs-utils firefox-gnome-support fonts-liberation fonts-takao-pgothic libreoffice-help-en-us
The following packages will be REMOVED
  ttf-kacst-one
The following NEW packages will be installed
  activity-log-manager-common activity-log-manager-control-center checkbox-qt cmap-adobe-japan2 fonts-kacst fonts-kacst-one
  fonts-khmeros-core fonts-lao fonts-nanum fonts-thai-tlwg fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono
  fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush
  fonts-tlwg-waree gir1.2-dee-1.0 gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 gir1.2-gudev-1.0
  gir1.2-indicate-0.7 gir1.2-rb-3.0 gir1.2-ubuntuoneui-3.0 gir1.2-unity-5.0 gnome-games-data landscape-client-ui-install
  libasyncns0:i386 libatk-adaptor-schemas libdiscid0 libdmapsharing-3.0-2 libfreerdp-plugins-standard libfreerdp1 libgdl-3-2
  libjson0:i386 libmusicbrainz3-6 libogg0:i386 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libqt4-sql-sqlite
  librhythmbox-core5 libssh-4 libubuntuoneui-3.0-1 libvncserver0 libwrap0:i386 libxcursor1:i386 libxrandr2:i386 mahjongg
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix python-aptdaemon.pkcompat python-debtagshw python-dirspec
  python-gi-cairo python-mako python-markupsafe python-packagekit python-ubuntu-sso-client remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone software-center-aptdaemon-plugins syslinux-legacy
  ubuntu-sso-client-gtk whoopsie xz-lzma
The following packages will be upgraded:
  adduser anjuta-common aptdaemon c2esp checkbox checkbox-gtk foo2zjs gnome-sudoku gnomine gtkpod gtkpod-data gwibber
  gwibber-service libanjuta-3-0 libgdl-3-common libgtkpod1 libindicate5 libsdl1.2debian min12xxw pnm2ppa ptouch-driver pxljr
  python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-indicate rastertosag-gdi
  splix ttf-khmeros-core ttf-thai-tlwg ubuntu-desktop ubuntu-sso-client usb-creator-common usb-creator-gtk
35 upgraded, 87 newly installed, 1 to remove and 717 not upgraded.
18 not fully installed or removed.
Need to get 31.0 MB of archives.
After this operation, 35.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libogg0 i386 1.2.2~dfsg-1ubuntu1 [17.6 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libxcursor1 i386 1:1.1.12-1 [23.0 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libxrandr2 i386 2:1.3.2-2 [17.7 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main adduser amd64 3.113ubuntu2 [133 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libasyncns0 i386 0.8-4 [12.9 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libjson0 i386 0.9-1ubuntu1 [16.7 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libwrap0 i386 7.6.q-21 [49.7 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libdiscid0 amd64 0.2.2-3 [12.8 kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libgdl-3-common amd64 3.3.91-1 [171 kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libgdl-3-2 amd64 3.3.91-1 [87.2 kB]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libqt4-sql-sqlite amd64 4:4.8.1-0ubuntu4 [22.4 kB]
Get:12 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libsdl1.2debian amd64 1.2.14-6.4ubuntu3 [197 kB]
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libssh-4 amd64 0.5.2-1 [119 kB]
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main whoopsie amd64 0.1.32 [24.6 kB]
Get:15 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main ubuntu-sso-client all 3.0.0-0ubuntu1 [3,064 B]
Get:16 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-ubuntu-sso-client all 3.0.0-0ubuntu1 [55.5 kB]
Get:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main xz-lzma all 5.1.1alpha+20110809-3 [12.4 kB]
Get:18 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main activity-log-manager-common all 0.9.4-0ubuntu3 [19.5 kB]
Get:19 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main activity-log-manager-control-center amd64 0.9.4-0ubuntu3 [74.1 kB]
Get:20 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libanjuta-3-0 amd64 2:3.4.0-1 [293 kB]
Get:21 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe anjuta-common all 2:3.4.0-1 [5,554 kB]
Get:22 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main c2esp all 23-1 [1,928 B]                                                       
Get:23 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main printer-driver-c2esp amd64 23-1 [41.7 kB]                                      
Get:24 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main checkbox-gtk all 0.13.7 [20.1 kB]                                              
Get:25 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main checkbox amd64 0.13.7 [1,439 kB]                                               
Get:26 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main checkbox-qt amd64 0.13.7 [70.6 kB]                                             
Get:27 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main cmap-adobe-japan2 all 0+20090930-2 [122 kB]                                    
Get:28 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-kacst all 2.01+mry-3 [479 kB]                                            
Get:29 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-kacst-one all 5.0+svn11846-2 [60.8 kB]                                   
Get:30 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe ttf-khmeros-core all 5.0-5ubuntu1 [1,542 B]                                
Get:31 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-khmeros-core all 5.0-5ubuntu1 [217 kB]                                   
Get:32 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-lao all 0.0.20060226-8 [54.1 kB]                                         
Get:33 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-nanum all 3.010-2 [7,742 kB]                                             
Get:34 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main ttf-thai-tlwg all 1:0.4.17-1ubuntu1 [4,134 B]                                  
Get:35 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-kinnari all 1:0.4.17-1ubuntu1 [284 kB]                              
Get:36 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-garuda all 1:0.4.17-1ubuntu1 [204 kB]                               
Get:37 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-norasi all 1:0.4.17-1ubuntu1 [417 kB]                               
Get:38 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-loma all 1:0.4.17-1ubuntu1 [194 kB]                                 
Get:39 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-mono all 1:0.4.17-1ubuntu1 [195 kB]                                 
Get:40 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-typewriter all 1:0.4.17-1ubuntu1 [198 kB]                           
Get:41 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-typist all 1:0.4.17-1ubuntu1 [213 kB]                               
Get:42 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-typo all 1:0.4.17-1ubuntu1 [212 kB]                                 
Get:43 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-umpush all 1:0.4.17-1ubuntu1 [283 kB]                               
Get:44 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-sawasdee all 1:0.4.17-1ubuntu1 [213 kB]                             
Get:45 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-purisa all 1:0.4.17-1ubuntu1 [374 kB]                               
Get:46 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-tlwg-waree all 1:0.4.17-1ubuntu1 [227 kB]                                
Get:47 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main fonts-thai-tlwg all 1:0.4.17-1ubuntu1 [7,396 B]                                
Get:48 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main foo2zjs all 20111202dfsg0-1ubuntu1 [2,048 B]                                   
Get:49 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main printer-driver-foo2zjs amd64 20111202dfsg0-1ubuntu1 [1,472 kB]                 
Get:50 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-dee-1.0 amd64 1.0.10-0ubuntu1 [13.3 kB]                                 
Get:51 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-gnomekeyring-1.0 amd64 3.2.2-2 [6,706 B]                                
Get:52 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-gstreamer-0.10 amd64 0.10.36-1ubuntu1 [114 kB]                          
Get:53 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-gst-plugins-base-0.10 amd64 0.10.36-1 [115 kB]                          
Get:54 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-gudev-1.0 amd64 175-0ubuntu9 [3,970 B]                                  
Get:55 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe python-indicate amd64 0.6.92-0ubuntu1 [15.5 kB]                            
Get:56 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libindicate5 amd64 0.6.92-0ubuntu1 [32.8 kB]                                   
Get:57 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-indicate-0.7 amd64 0.6.92-0ubuntu1 [7,340 B]                            
Get:58 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main librhythmbox-core5 amd64 2.96-0ubuntu4 [534 kB]                                
Get:59 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-rb-3.0 amd64 2.96-0ubuntu4 [44.6 kB]                                    
Get:60 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libubuntuoneui-3.0-1 amd64 3.0.0-0ubuntu1 [57.5 kB]                            
Get:61 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-ubuntuoneui-3.0 amd64 3.0.0-0ubuntu1 [2,590 B]                          
Get:62 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gir1.2-unity-5.0 amd64 5.10.0-0ubuntu1 [9,910 B]                               
Get:63 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gnome-games-data all 1:3.4.1-0ubuntu1 [106 kB]                                 
Get:64 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-gi-cairo amd64 3.2.0-3 [5,202 B]                                        
Get:65 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gnome-sudoku all 1:3.4.1-0ubuntu1 [763 kB]                                     
Get:66 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gnomine amd64 1:3.4.1-0ubuntu1 [411 kB]                                        
Get:67 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gwibber amd64 3.4.0-0ubuntu4 [156 kB]                                          
Get:68 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main gwibber-service all 3.4.0-0ubuntu4 [40.1 kB]                                   
Get:69 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main aptdaemon all 0.43+bzr805-0ubuntu1 [14.6 kB]                                   
Get:70 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe python-aptdaemon-gtk all 0.43+bzr805-0ubuntu1 [1,668 B]                    
Get:71 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe python-aptdaemon.gtkwidgets all 0.43+bzr805-0ubuntu1 [13.9 kB]             
Get:72 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-aptdaemon.gtk3widgets all 0.43+bzr805-0ubuntu1 [14.8 kB]                
Get:73 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-aptdaemon all 0.43+bzr805-0ubuntu1 [82.4 kB]                            
Get:74 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main landscape-client-ui-install amd64 12.04.3-0ubuntu1 [8,200 B]                   
Get:75 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libatk-adaptor-schemas amd64 2.4.0-1ubuntu2 [2,104 B]                          
Get:76 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libdmapsharing-3.0-2 amd64 2.9.14-1 [78.6 kB]                                  
Get:77 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libfreerdp1 amd64 1.0.1-1ubuntu2 [242 kB]                                      
Get:78 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libfreerdp-plugins-standard amd64 1.0.1-1ubuntu2 [74.3 kB]                     
Get:79 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libmusicbrainz3-6 amd64 3.0.2-2.1 [128 kB]                                     
Get:80 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libproxy1-plugin-gsettings amd64 0.4.7-0ubuntu4 [21.9 kB]                      
Get:81 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libproxy1-plugin-networkmanager amd64 0.4.7-0ubuntu4 [6,082 B]                 
Get:82 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libvncserver0 amd64 0.9.8.2-2ubuntu1 [186 kB]                                  
Get:83 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main mahjongg amd64 1:3.4.1-0ubuntu1 [2,331 kB]                                     
Get:84 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main min12xxw all 0.0.9-6ubuntu1 [1,700 B]                                          
Get:85 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main printer-driver-min12xxw amd64 0.0.9-6ubuntu1 [48.4 kB]                         
Get:86 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main pnm2ppa all 1.13+nondbs-0ubuntu1 [1,648 B]                                     
Get:87 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main printer-driver-pnm2ppa amd64 1.13+nondbs-0ubuntu1 [210 kB]                     
Get:88 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main ptouch-driver all 1.3-3 [1,944 B]                                              
Get:89 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main printer-driver-ptouch amd64 1.3-3 [29.1 kB]                                    
Get:90 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main pxljr all 1.3+repack0-2 [3,564 B]                                              
Get:91 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main printer-driver-pxljr amd64 1.3+repack0-2 [30.8 kB]                             
Get:92 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe rastertosag-gdi all 0.1-3 [1,460 B]                                        
Get:93 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main printer-driver-sag-gdi all 0.1-3 [9,112 B]                                     
Get:94 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main splix all 2.0.0+svn300-1.1ubuntu2 [1,782 B]                                    
Get:95 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main printer-driver-splix amd64 2.0.0+svn300-1.1ubuntu2 [71.3 kB]                   
Get:96 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-debtagshw all 1.9+git20120320 [9,990 B]                                 
Get:97 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-markupsafe amd64 0.15-1 [13.6 kB]                                       
Get:98 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-mako all 0.5.0-1 [53.2 kB]                                              
Get:99 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main remmina-common all 1.0.0-1ubuntu5 [47.1 kB]                                    
Get:100 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main remmina amd64 1.0.0-1ubuntu5 [131 kB]                                         
Get:101 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main remmina-plugin-rdp amd64 1.0.0-1ubuntu5 [28.6 kB]                             
Get:102 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main remmina-plugin-vnc amd64 1.0.0-1ubuntu5 [21.1 kB]                             
Get:103 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main rhythmbox-data all 2.96-0ubuntu4 [444 kB]                                     
Get:104 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main rhythmbox amd64 2.96-0ubuntu4 [167 kB]                                        
Get:105 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main rhythmbox-mozilla amd64 2.96-0ubuntu4 [5,856 B]                               
Get:106 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main rhythmbox-plugin-cdrecorder amd64 2.96-0ubuntu4 [16.3 kB]                     
Get:107 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main rhythmbox-plugin-magnatune amd64 2.96-0ubuntu4 [23.6 kB]                      
Get:108 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main rhythmbox-plugin-zeitgeist all 2.96-0ubuntu4 [50.0 kB]                        
Get:109 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main rhythmbox-plugins amd64 2.96-0ubuntu4 [327 kB]                                
Get:110 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main software-center-aptdaemon-plugins all 0.1.2 [5,352 B]                         
Get:111 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main syslinux-legacy amd64 2:3.63+dfsg-2ubuntu5 [48.0 kB]                          
Get:112 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main ubuntu-desktop amd64 1.267 [3,928 B]                                          
Get:113 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main usb-creator-gtk amd64 0.2.38 [26.7 kB]                                        
Get:114 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main usb-creator-common amd64 0.2.38 [23.8 kB]                                     
Get:115 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe gtkpod amd64 2.1.1-1 [327 kB]                                             
Get:116 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe gtkpod-data all 2.1.1-1 [1,293 kB]                                        
Get:117 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libgtkpod1 amd64 2.1.1-1 [142 kB]                                         
Get:118 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-packagekit all 0.7.2-4ubuntu3 [22.4 kB]                                
Get:119 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-aptdaemon.pkcompat all 0.43+bzr805-0ubuntu1 [28.9 kB]                  
Get:120 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main python-dirspec all 3.0.0-0ubuntu1 [5,286 B]                                   
Get:121 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main rhythmbox-ubuntuone all 3.0.0-0ubuntu1 [7,256 B]                              
Get:122 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main ubuntu-sso-client-gtk all 3.0.0-0ubuntu1 [14.8 kB]                            
Fetched 31.0 MB in 60s (514 kB/s)                                                                                                    
Extract templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/available' near line 10527 package 'skype-wrapper':
 blank line in value of field 'Description'
E: Sub-process /usr/bin/dpkg returned an error code (2)
[23:29:48] &#1046;&#1086;&#1088;&#1086;: georgi@GolfDeltaZulu:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1c00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4200004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4400014

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e019d8

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e01a06

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:3151): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed

Screen geometry changed:
   0x0x1280x800

Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x120009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x12000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x12000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x12000a7!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x12000a7!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x12000aa!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/gnome-terminal.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-04-28 23:27:54 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-04-28 23:27:54 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
Initializing staticswitcher options...done
ERROR 2012-04-28 23:27:55 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
WARN  2012-04-28 23:27:59 unity.iconloader IconLoader.cpp:536 Unable to load icon file:///usr/share/unity/4/lens-nav-app.svg at size 24: Error opening file: No such file or directory
WARN  2012-04-28 23:27:59 unity.iconloader IconLoader.cpp:536 Unable to load icon file:///usr/share/unity/4/lens-nav-file.svg at size 24: Error opening file: No such file or directory
WARN  2012-04-28 23:27:59 unity.iconloader IconLoader.cpp:536 Unable to load icon file:///usr/share/unity/4/lens-nav-music.svg at size 24: Error opening file: No such file or directory
WARN  2012-04-28 23:28:01 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "SetViewType" on object path: "/com/canonical/unity/lens/files" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method `SetViewType'
WARN  2012-04-28 23:28:01 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "SetViewType" on object path: "/com/canonical/unity/lens/music" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method `SetViewType'
WARN  2012-04-28 23:28:01 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-applications/unity-applications-daemon received signal 5
WARN  2012-04-28 23:28:01 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-applications/unity-applications-daemon received signal 5
WARN  2012-04-28 23:28:01 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method Search proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-04-28 23:28:01 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method Search proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-04-28 23:28:09 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "SetViewType" on object path: "/com/canonical/unity/lens/files" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method `SetViewType'
WARN  2012-04-28 23:28:09 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "SetViewType" on object path: "/com/canonical/unity/lens/music" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method `SetViewType'
```

---

### Post by oldfred on 2012-04-28
Added code tags. Please highlight like copying and click on the # in the edit panel above you message to add code tags.

Can you get to recovery mode?

---

### Post by stahan on 2012-04-28
I am in recovery mode

---

### Post by stahan on 2012-04-28
I ran fsck and dpkg, but i got the same output as posted previously

---

### Post by oldfred on 2012-04-28
What does this show? Is everything precise?

 cat /etc/apt/sources.list

Try these if sources is correct:

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

