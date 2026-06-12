---
title: "Partial Upgrade"
date: 2010-07-13
forum: General Help
---

### Post by rules on 2010-07-13
Hi all

Every time I do an update, there are always a couple of things that stay behind in the list and it will ask me to do a partial upgrade, but it never does (just says calculating changes and then eventually fails).

The list of untouchables is getting longer and longer. Is there a way of figuring out what's happening (or not happening :)).

Thanks.

---

### Post by philinux on 2010-07-13
```

```You don't say what version you're running. However.

Open a terminal.
sudo aptitude update && sudo aptitude safe-upgrade

---

### Post by tekkidd on 2010-07-13
Try This: 

```
sudo apt-get update
```
then 
```
sudo apt-get upgrade
```
then 
```
sudo apt-get dist-upgrade
```

---

### Post by rules on 2010-07-13
Lucid ... as per my sig :)

Writing extended state information... Done
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid Release.gpg                              
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_ZA           
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_ZA     
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_ZA       
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_ZA     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates Release.gpg                      
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_ZA   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_ZA        
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_ZA    
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) etch Release.gpg                                   
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) etch/main Translation-en_ZA                
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                         
Ign [http://ppa.launchpad.net/synce/ubuntu/](http://ppa.launchpad.net/synce/ubuntu/) lucid/main Translation-en_ZA         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed Release.gpg                     
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_ZA  
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports Release.gpg                    
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_ZA 
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_ZA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                           
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) etch Release                                       
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                      
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid Release                                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates Release                          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed Release                         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                         
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) etch/main Packages                                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                          
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) etch/main Packages                                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/main Sources                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/universe Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/universe Sources              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/main Sources          
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) etch/main Packages                      
  404  Not Found
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/restricted Sources    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed/restricted Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed/main Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed/universe Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports/multiverse Packages            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports/universe Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources                
Fetched 308B in 9s (33B/s)                                                      
Reading package lists... Done             
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D



That last bit doesn't look good, what's it mean?

---

### Post by rules on 2010-07-13
tekkidd ... this is what your commands return

rafiq@rafiq-laptop:~$ sudo apt-get update
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_ZA          
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Ign [http://ppa.launchpad.net/synce/ubuntu/](http://ppa.launchpad.net/synce/ubuntu/) lucid/main Translation-en_ZA        
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_ZA    
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_ZA      
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_ZA    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_ZA  
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed Release.gpg                    
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_ZA 
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_ZA
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid Release                                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates Release                         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_ZA   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/main Packages                           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/main Sources                            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed/restricted Packages            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed/main Packages                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed/multiverse Packages            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-proposed/universe Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports/restricted Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports/main Packages                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports/multiverse Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-backports/universe Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_ZA       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                  
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) etch Release.gpg                                  
  Could not connect to ftp.de.debian.org:80 (141.76.2.4). - connect (110: Connection timed out)
Err [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) etch/main Translation-en_ZA
  Unable to connect to ftp.de.debian.org:http:
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) etch Release         
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) etch/main Packages
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) etch/main Packages
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) etch/main Packages
  Unable to connect to ftp.de.debian.org:http:
Fetched 308B in 21s (15B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
W: Failed to fetch [http://ftp.de.debian.org/debian/dists/etch/Release.gpg](http://ftp.de.debian.org/debian/dists/etch/Release.gpg)  Could not connect to ftp.de.debian.org:80 (141.76.2.4). - connect (110: Connection timed out)

W: Failed to fetch [http://ftp.de.debian.org/debian/dists/etch/main/i18n/Translation-en_ZA.bz2](http://ftp.de.debian.org/debian/dists/etch/main/i18n/Translation-en_ZA.bz2)  Unable to connect to ftp.de.debian.org:http:

W: Failed to fetch [http://ftp.de.debian.org/debian/dists/etch/main/binary-i386/Packages.gz](http://ftp.de.debian.org/debian/dists/etch/main/binary-i386/Packages.gz)  Unable to connect to ftp.de.debian.org:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
rafiq@rafiq-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libavc1394-0 linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
rafiq@rafiq-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  acpi-support acpid alsa-base alsa-utils apparmor-utils apport apport-gtk at
  at-spi avahi-daemon avahi-utils bluez bluez-cups brltty-x11 couchdb-bin cron
  cups cups-driver-gutenprint desktopcouch erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evolution-couchdb foo2zjs foomatic-db
  foomatic-db-engine friendly-recovery ftp gdebi-kde gdm gdm-guest-session
  ghostscript-cups gimp gnome-applets gnome-bluetooth gnome-control-center
  gnome-media gnome-orca gnome-panel gnome-screensaver gnome-session
  gnome-session-bin gnome-settings-daemon gnome-system-tools gnome-user-share
  google-chrome-beta gstreamer0.10-pulseaudio gwibber gwibber-service hplip
  icedtea6-plugin icoutils indicator-applet indicator-applet-session
  indicator-me indicator-sound install-package irqbalance kdebase-runtime
  kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdelibs-bin kdelibs5 kdepim-runtime
  kdepimlibs5 kdesudo kpackagekit kubuntu-debug-installer lftp
  libaccess-bridge-java libaccess-bridge-java-jni libasound2-plugins
  libcanberra-pulse libfluidsynth1 libgegl-0.0-0 libjorbis-java libjspeex-java
  libkfontinst4 libkscreensaver5 libksgrd4 libkworkspace4 libmp3spi-java
  libnet-dbus-perl libnss-mdns liboobs-1-4 libplasma-applet-system-monitor4
  libplasma3 libplasmaclock4 libplasmagenericshell4 libprocesscore4
  libprocessui4 libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  librpc-xml-perl libsdl1.2debian libsdl1.2debian-pulseaudio libsolidcontrol4
  libswt-gtk-3.5-java libswt-gtk-3.5-jni libtaskmanager4 libtritonus-bin
  libvorbisspi-java libweather-ion4 libwww-perl libxine1 libxine1-misc-plugins
  libxine1-x libxml-parser-perl libxml-sax-expat-perl libxml-twig-perl
  libxml-xpath-perl libxss1 libxtst6 libxvmc1 libxxf86dga1
  linux-image-2.6.32-21-generic linux-sound-base mousetweaks network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome
  ntpdate onboard openjdk-6-jre openoffice.org-base-core openoffice.org-calc
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-math openoffice.org-writer
  openprinting-ppds opensync-plugin-synce pcmciautils phonon
  phonon-backend-xine pidgin pidgin-libnotify plasma-dataengines-workspace
  plasma-scriptengine-javascript plasma-widgets-workspace plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11 pm-utils
  pm-utils-powersave-policy polkit-kde-1 powermgmt-base ppp pppconfig
  pppoeconf pptp-linux pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils pxljr python-desktopcouch python-desktopcouch-records
  python-kde4 python-pyatspi python-speechd python-uno python-virtkey rsyslog
  skype software-properties-kde speech-dispatcher splix synce-hal
  synce-sync-engine system-tools-backends telepathy-salut telnet totem
  totem-mozilla totem-plugins ttf-mscorefonts-installer ubuntu-desktop
  ubuntu-minimal ubuntu-standard ufw update-manager-kde ureadahead vino wine
  wine1.2 x-ttcidfont-conf x11-apps x11-session-utils x11-utils x11-xfs-utils
  x11-xserver-utils xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings
  xfonts-mathml xfonts-scalable xfonts-utils xinit xorg xserver-xorg-input-all
  xserver-xorg-video-all xserver-xorg-video-intel
  xserver-xorg-video-openchrome zekr
The following NEW packages will be installed:
  diff libraw1394-8 linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
  mktemp
The following packages have been kept back:
  linux-generic linux-image-generic
The following packages will be upgraded:
  libavc1394-0 linux-headers-generic
2 upgraded, 5 newly installed, 223 to remove and 2 not upgraded.
Need to get 10.7MB/10.7MB of archives.
After this operation, 726MB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libraw1394-8 libavc1394-0
Install these packages without verification [y/N]? y
Get:1 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/universe diff 1:2.8.1-18 [5,868B]
Get:2 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main mktemp 7.4-2ubuntu2 [14.2kB]
Err [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) etch/main libraw1394-8 1.2.1-2    
  404  Not Found
Get:3 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/main linux-headers-2.6.32-24 2.6.32-24.38 [9,878kB]
Get:4 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/main linux-headers-2.6.32-24-generic 2.6.32-24.38 [740kB]
Get:5 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-proposed/main linux-headers-generic 2.6.32.24.25 [4,022B]
Fetched 10.6MB in 7min 4s (25.1kB/s)                                           
Failed to fetch [http://ftp.de.debian.org/debian/pool/main/libr/libraw1394/libraw1394-8_1.2.1-2_i386.deb](http://ftp.de.debian.org/debian/pool/main/libr/libraw1394/libraw1394-8_1.2.1-2_i386.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
rafiq@rafiq-laptop:~$

---

### Post by philinux on 2010-07-14
@rules,

HOWTO: Fix GPG errors

[http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

---

### Post by dcstar on 2010-07-14
> **rules said:**
> tekkidd ... this is what your commands return

rafiq@rafiq-laptop:~$ sudo apt-get update
.........                                      
Failed to fetch **[http://ftp.de.debian.org/debian/pool/main**/libr/libraw1394/libraw1394-8_1.2.1-2_i386.deb](http://ftp.de.debian.org/debian/pool/main**/libr/libraw1394/libraw1394-8_1.2.1-2_i386.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
rafiq@rafiq-laptop:~$

Anyone silly enough to mix Debian repositories with Ubuntu ones will have ongoing problems with packages having unsatisfied dependencies and therefore being unable to be upgraded or installed.

---

### Post by rules on 2010-07-14
> **dcstar said:**
> Anyone silly enough to mix Debian repositories with Ubuntu ones will have ongoing problems with packages having unsatisfied dependencies and therefore being unable to be upgraded or installed.

WHAT ... no really, what you talking about :-k

---

### Post by rules on 2010-07-14
Thanks Phil, that GPG thing worked and also dc, I removed the Debian entry and is fine again. I can't remember why that got added in the first place, but the strange thing is it states that it's "Officially Supported".

Ah well, it works, THANKS ;)

---

