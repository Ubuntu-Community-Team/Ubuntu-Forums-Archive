---
title: "purging apt's package lists"
date: 2010-08-01
forum: General Help
---

### Post by jvofvnopz on 2010-08-01
I have had problems with updating some of my programs with apt. For example, using "apt-cache show firefox", it lists three different versions (one from the Launchpad PPA and two from the official Ubuntu repos (lucid-updates and lucid respectively)):
```

Package: firefox
Source: firefox
Priority: optional
Section: web
Installed-Size: 29828
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: i386
Version: 3.6.9~hg20100727r34466+nobinonly-0ubuntu1~umd1~lucid
Recommends: ubufox
Suggests: firefox-gnome-support (= 3.6.9~hg20100727r34466+nobinonly-0ubuntu1~umd1~lucid), kmozillahelper (>= 0.6), latex-xft-fonts, libthai0
Provides: www-browser
Depends: fontconfig, psmisc, lsb-release, debianutils (>= 1.16), libasound2 (>> 1.0.22), libatk1.0-0 (>= 1.29.3), libc6 (>= 2.11), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.23.5), libgtk2.0-0 (>= 2.18.0), libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d (>= 3.12.6), libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.1.1), libx11-6 (>= 0), libxext6, libxrender1, libxt6, zlib1g (>= 1:1.1.4), firefox-branding | abrowser-branding
Filename: pool/main/f/firefox/firefox_3.6.9~hg20100727r34466+nobinonly-0ubuntu1~umd1~lucid_i386.deb
Size: 11333330
MD5sum: ee31615398e0a78f18953efa93d720a5
SHA1: af103f4679f24a15ef111f3b284adcd2f5649f88
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.

Package: firefox
Priority: optional
Section: web
Installed-Size: 29664
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: i386
Version: 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
Replaces: firefox-2, firefox-2-dom-inspector, firefox-2-libthai, firefox-3.0, firefox-3.5, firefox-3.6, firefox-3.6-gnome-support
Provides: firefox-2, firefox-2-dom-inspector, firefox-2-libthai, firefox-3.0, firefox-3.5, firefox-3.6, www-browser
Depends: fontconfig, psmisc, lsb-release, debianutils (>= 1.16), libasound2 (>> 1.0.22), libatk1.0-0 (>= 1.29.3), libc6 (>= 2.11), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.23.5), libgtk2.0-0 (>= 2.18.0), libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d (>= 3.12.6), libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.1.1), libx11-6 (>= 0), libxext6, libxrender1, libxt6, zlib1g (>= 1:1.1.4), firefox-branding | abrowser-branding
Recommends: ubufox
Suggests: firefox-gnome-support (= 3.6.8+build1+nobinonly-0ubuntu0.10.04.1), kmozillahelper (>= 0.6), latex-xft-fonts, libthai0
Conflicts: firefox-2 (<< 3), firefox-2-dom-inspector (<< 3), firefox-2-libthai (<< 3), firefox-3.0 (<< 3.6~hg20100117r33523), firefox-3.5 (<< 3.6~hg20100117r33523), firefox-3.6 (<< 3.6~hg20100117r33523), firefox-3.6-gnome-support (<< 3.6~hg20100117r33523)
Filename: pool/main/f/firefox/firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb
Size: 11244270
MD5sum: 693ca6132141f4a9752e9cc9792762a8
SHA1: a4d773a4c5ffd45bb154938d190e2b30fde8a4e1
SHA256: b54beb09e54718718f75233312679ef6496a4be26b36b1c3b782c84f6167a216
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Xul-Appid: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntu-desktop, edubuntu-desktop, xubuntu-desktop, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, ubuntu-netbook

Package: firefox
Priority: optional
Section: web
Installed-Size: 28668
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: i386
Version: 3.6.3+nobinonly-0ubuntu4
Replaces: firefox-2, firefox-2-dom-inspector, firefox-2-libthai, firefox-3.0, firefox-3.5, firefox-3.6, firefox-3.6-gnome-support
Provides: firefox-2, firefox-2-dom-inspector, firefox-2-libthai, firefox-3.0, firefox-3.5, firefox-3.6, www-browser
Depends: fontconfig, psmisc, lsb-release, debianutils (>= 1.16), libasound2 (>> 1.0.22), libatk1.0-0 (>= 1.29.3), libc6 (>= 2.11), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.23.5), libgtk2.0-0 (>= 2.18.0), libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d (>= 3.12.6), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.1.1), libx11-6 (>= 0), libxext6, libxrender1, libxt6, zlib1g (>= 1:1.1.4), firefox-branding | abrowser-branding
Recommends: ubufox
Suggests: firefox-gnome-support (= 3.6.3+nobinonly-0ubuntu4), kmozillahelper (>= 0.6), latex-xft-fonts, libthai0
Conflicts: firefox-2 (<< 3), firefox-2-dom-inspector (<< 3), firefox-2-libthai (<< 3), firefox-3.0 (<< 3.6~hg20100117r33523), firefox-3.5 (<< 3.6~hg20100117r33523), firefox-3.6 (<< 3.6~hg20100117r33523), firefox-3.6-gnome-support (<< 3.6~hg20100117r33523)
Filename: pool/main/f/firefox/firefox_3.6.3+nobinonly-0ubuntu4_i386.deb
Size: 10855668
MD5sum: bccbd43d3becac11054df033dd0bf529
SHA1: 7406f18986cbcd49ee7f249115c9e19c2860ab2e
SHA256: 16f0a85e15987e5b463eb29fd039064b9d20326368111ad4333a11ca46411670
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Xul-Appid: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntu-desktop, edubuntu-desktop, xubuntu-desktop, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, ubuntu-netbook


```Now, I noticed that only the Launchpad version is out-of-date. In fact, when I checked the site ([https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")) it showed the latest version of the firefox package to be 3.6.9~hg20100730r34471+nobinonly-0ubuntu1~umd1~lucid. I tried running "apt-get update", but this still didn't help.

Therefore, I want to find a way to purge the package lists (the stuff that's downloaded during "apt-get update") and force apt to download the latest package lists. Is this possible? Also, is it possible that this is a bug in apt?

EDIT:
When I run apt-get update, it displays as follows:
```
Hit http://apt.wakoopa.com all Release.gpg
Ign http://apt.wakoopa.com/ all/main Translation-en_US
Hit http://apt.wakoopa.com all Release                                                                                   
Hit http://linux.dropbox.com lucid Release.gpg                                                                           
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Ign http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ lucid/main Translation-en_US                           
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Hit http://archive.canonical.com lucid Release.gpg                                                                       
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US                                                        
Hit http://apt.last.fm debian Release.gpg                                                                                
Hit http://archive.ubuntu.com lucid Release.gpg                                                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                                                 
Hit http://packages.medibuntu.org lucid Release.gpg                                                                      
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                                                          
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US                                                      
Hit http://linux.dropbox.com lucid Release                                                                               
Ign http://ppa.launchpad.net/troorl/pino/ubuntu/ lucid/main Translation-en_US                                            
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Ign http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ lucid/main Translation-en_US                               
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US                                        
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Ign http://ppa.launchpad.net/vala-team/ppa/ubuntu/ lucid/main Translation-en_US                                          
Hit http://ppa.launchpad.net lucid Release                                                                               
Hit http://archive.canonical.com lucid Release                                                                           
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                                 
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                                                  
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                               
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                         
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                           
Hit http://apt.wakoopa.com all/main Packages                                                                             
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                         
Hit http://archive.ubuntu.com lucid-security Release.gpg                                                         
Hit http://packages.medibuntu.org lucid Release                                                                          
Hit http://linux.dropbox.com lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid Release                                                                               
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Ign http://apt.last.fm/ debian/stable Translation-en_US                                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                                      
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                                        
Hit http://archive.ubuntu.com lucid Release                                                                              
Hit http://archive.ubuntu.com lucid-updates Release                                                                      
Hit http://archive.canonical.com lucid/partner Packages                                                                  
Hit http://packages.medibuntu.org lucid/free Packages                                                                    
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://archive.ubuntu.com lucid-security Release                                                                     
Hit http://archive.canonical.com lucid/partner Sources                                                                   
Hit http://ppa.launchpad.net lucid/main Packages                                                                 
Hit http://packages.medibuntu.org lucid/non-free Packages                                  
Hit http://packages.medibuntu.org lucid/free Sources                                       
Hit http://packages.medibuntu.org lucid/non-free Sources                                   
Hit http://archive.ubuntu.com lucid/main Sources                                           
Hit http://archive.ubuntu.com lucid/restricted Sources               
Hit http://archive.ubuntu.com lucid/main Packages                    
Hit http://apt.last.fm debian Release                                
Hit http://archive.ubuntu.com lucid/restricted Packages              
Hit http://archive.ubuntu.com lucid/multiverse Sources               
Hit http://archive.ubuntu.com lucid/universe Sources                 
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://archive.ubuntu.com lucid/universe Packages                 
Hit http://archive.ubuntu.com lucid/multiverse Packages               
Get:1 http://archive.ubuntu.com lucid-updates/main Packages [272kB]   
Get:2 http://archive.ubuntu.com lucid-updates/restricted Packages [3,252B]
Get:3 http://archive.ubuntu.com lucid-updates/restricted Sources [1,292B]
Get:4 http://archive.ubuntu.com lucid-updates/main Sources [97.6kB]
Get:5 http://archive.ubuntu.com lucid-updates/multiverse Sources [1,499B]
Get:6 http://archive.ubuntu.com lucid-updates/universe Sources [26.2kB]   
Get:7 http://archive.ubuntu.com lucid-updates/universe Packages [81.8kB]     
Get:8 http://archive.ubuntu.com lucid-updates/multiverse Packages [3,771B]    
Ign http://apt.last.fm debian/stable Packages                                 
Get:9 http://archive.ubuntu.com lucid-security/main Packages [52.6kB]
Get:10 http://archive.ubuntu.com lucid-security/restricted Packages [14B]                            
Get:11 http://archive.ubuntu.com lucid-security/restricted Sources [14B]                        
Get:12 http://archive.ubuntu.com lucid-security/main Sources [17.3kB]                          
Get:13 http://archive.ubuntu.com lucid-security/multiverse Sources [580B]
Get:14 http://archive.ubuntu.com lucid-security/universe Sources [5,460B]                   
Get:15 http://archive.ubuntu.com lucid-security/universe Packages [27.2kB]                  
Get:16 http://archive.ubuntu.com lucid-security/multiverse Packages [2,012B]                    
Ign http://apt.last.fm debian/stable Packages                                                   
Hit http://apt.last.fm debian/stable Packages     
Fetched 16B in 2s (8B/s)    
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[root][Sunday 17:59:16]$ upd                                                                           [/home/luolimao9] 
Hit http://apt.wakoopa.com all Release.gpg
Ign http://apt.wakoopa.com/ all/main Translation-en_US
Hit http://apt.wakoopa.com all Release                                                                                   
Hit http://linux.dropbox.com lucid Release.gpg                                                                           
Hit http://archive.canonical.com lucid Release.gpg                                                                       
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US                                                        
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Ign http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ lucid/main Translation-en_US                           
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Hit http://apt.last.fm debian Release.gpg                                                                                
Hit http://archive.ubuntu.com lucid Release.gpg                                                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                       
Hit http://apt.wakoopa.com all/main Packages                                                                             
Hit http://packages.medibuntu.org lucid Release.gpg                                                                      
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                                                          
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US                                                      
Hit http://linux.dropbox.com lucid Release                                                                               
Hit http://archive.canonical.com lucid Release                                                                           
Ign http://ppa.launchpad.net/troorl/pino/ubuntu/ lucid/main Translation-en_US                                            
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Ign http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ lucid/main Translation-en_US                               
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US                                        
Hit http://ppa.launchpad.net lucid Release.gpg                                                                           
Ign http://ppa.launchpad.net/vala-team/ppa/ubuntu/ lucid/main Translation-en_US                                          
Hit http://ppa.launchpad.net lucid Release                                                                               
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                                 
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                                                  
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                 
Hit http://archive.ubuntu.com lucid-security Release.gpg                                                         
Hit http://packages.medibuntu.org lucid Release                                                                          
Hit http://linux.dropbox.com lucid/main Packages                                                                         
Ign http://apt.last.fm/ debian/stable Translation-en_US                                                          
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Hit http://ppa.launchpad.net lucid Release                                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                
Hit http://ppa.launchpad.net lucid Release                                                                               
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                                        
Hit http://archive.ubuntu.com lucid Release                                                                              
Hit http://archive.ubuntu.com lucid-updates Release                                                                      
Hit http://archive.canonical.com lucid/partner Packages                                                                  
Hit http://packages.medibuntu.org lucid/free Packages                                                                    
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                 
Hit http://archive.ubuntu.com lucid-security Release                                                             
Hit http://apt.last.fm debian Release                                                                            
Hit http://archive.canonical.com lucid/partner Sources                                                           
Hit http://packages.medibuntu.org lucid/non-free Packages                                                        
Hit http://packages.medibuntu.org lucid/free Sources                 
Hit http://packages.medibuntu.org lucid/non-free Sources             
Hit http://archive.ubuntu.com lucid/main Sources                                            
Hit http://archive.ubuntu.com lucid/restricted Sources                                      
Hit http://archive.ubuntu.com lucid/main Packages                                           
Hit http://archive.ubuntu.com lucid/restricted Packages                                     
Hit http://archive.ubuntu.com lucid/multiverse Sources                                      
Hit http://archive.ubuntu.com lucid/universe Sources                                        
Hit http://archive.ubuntu.com lucid/universe Packages                                       
Hit http://archive.ubuntu.com lucid/multiverse Packages                                     
Hit http://archive.ubuntu.com lucid-updates/main Packages            
Hit http://archive.ubuntu.com lucid-updates/restricted Packages      
Hit http://archive.ubuntu.com lucid-updates/restricted Sources       
Hit http://archive.ubuntu.com lucid-updates/main Sources             
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources       
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                     
Ign http://apt.last.fm debian/stable Packages                        
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages         
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages       
Hit http://archive.ubuntu.com lucid-security/main Packages            
Hit http://archive.ubuntu.com lucid-security/restricted Packages      
Hit http://archive.ubuntu.com lucid-security/restricted Sources       
Hit http://archive.ubuntu.com lucid-security/main Sources             
Hit http://archive.ubuntu.com lucid-security/multiverse Sources       
Hit http://archive.ubuntu.com lucid-security/universe Sources         
Hit http://archive.ubuntu.com lucid-security/universe Packages        
Ign http://apt.last.fm debian/stable Packages                         
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://apt.last.fm debian/stable Packages   
Reading package lists... Done                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by jvofvnopz on 2010-08-02
Never mind, the issue has somehow cleared up.

---

