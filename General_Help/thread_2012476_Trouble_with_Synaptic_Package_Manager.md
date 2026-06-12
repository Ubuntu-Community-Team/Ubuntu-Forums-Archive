---
title: "Trouble with Synaptic Package Manager"
date: 2012-06-29
forum: General Help
---

### Post by thx1137 on 2012-06-29
Hi,

I wanted to change something in Settings -> Repositories in the Synaptic Package Manager today, but I only get a message box saying

Repositories changed
The repository information has changed. You have to click on the "Reload" button for your changes to take effect

but it does not help. I get the same message box again. When I run the Synaptic Package Manager from console, it produces the following error output when I want to open the Repositories window:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 85, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 584, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

anybody has any idea what is happening? I use Ubuntu 12.04 LTS

---

### Post by plucky on 2012-06-29
> **thx1137 said:**
> Hi,

I wanted to change something in Settings -> Repositories in the Synaptic Package Manager today, but I only get a message box saying

Repositories changed
The repository information has changed. You have to click on the "Reload" button for your changes to take effect

but it does not help. I get the same message box again. When I run the Synaptic Package Manager from console, it produces the following error output when I want to open the Repositories window:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 85, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 584, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

anybody has any idea what is happening? I use Ubuntu 12.04 LTS


Open a Terminal window and run ```
sudo apt-get update
``` which is the same as "Reloading" the repositories.

Post the output if there are any errors.

---

### Post by thx1137 on 2012-06-29
```
milan@milan-desktop:~$ sudo apt-get update
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise InRelease
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise Release.gpg                           
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise Release                               
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates Release                       
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports Release                     
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/main Sources                          
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/universe Sources                      
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/main amd64 Packages           
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/restricted amd64 Packages     
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/universe amd64 Packages       
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/multiverse amd64 Packages     
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Reading package lists... Done
```

---

### Post by plucky on 2012-06-29
No errors there.

What does ```
sudo apt-get upgrade
``` show you?

---

### Post by thx1137 on 2012-06-30
milan@milan-desktop:~$ sudo apt-get upgrade
[sudo] password for milan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  accountsservice firefox firefox-globalmenu firefox-gnome-support
  firefox-locale-en gir1.2-gtk-3.0 gir1.2-nautilus-3.0 gnome-settings-daemon
  gwibber gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter libaccountsservice0 libgail-3-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgwibber-gtk2 libgwibber2
  libnautilus-extension1a libsmbclient libwbclient0 linux-libc-dev nautilus
  nautilus-data python-crypto samba-common samba-common-bin smbclient
  software-center thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us unity-lens-video xdiagnose
  xserver-xorg-input-evdev xserver-xorg-input-vmmouse
40 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 70.7 MB of archives.
After this operation, 638 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libgtk-3-bin amd64 3.4.2-0ubuntu0.3 [15.9 kB]
Get:2 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libgail-3-0 amd64 3.4.2-0ubuntu0.3 [24.0 kB]
Get:3 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libgtk-3-0 amd64 3.4.2-0ubuntu0.3 [2,284 kB]
Get:4 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libgtk-3-common all 3.4.2-0ubuntu0.3 [145 kB]
Get:5 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libwbclient0 amd64 2:3.6.3-2ubuntu2.3 [30.3 kB]
Get:6 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libsmbclient amd64 2:3.6.3-2ubuntu2.3 [2,159 kB]
Get:7 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main accountsservice amd64 0.6.15-2ubuntu9.1 [44.1 kB]
Get:8 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libaccountsservice0 amd64 0.6.15-2ubuntu9.1 [30.5 kB]
Get:9 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main firefox-globalmenu amd64 13.0.1+build1-0ubuntu0.12.04.1 [48.2 kB]
Get:10 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main firefox amd64 13.0.1+build1-0ubuntu0.12.04.1 [18.7 MB]
Get:11 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main firefox-gnome-support amd64 13.0.1+build1-0ubuntu0.12.04.1 [9,268 B]
Get:12 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main firefox-locale-en amd64 13.0.1+build1-0ubuntu0.12.04.1 [434 kB]
Get:13 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-gtk-3.0 amd64 3.4.2-0ubuntu0.3 [236 kB]
Get:14 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libnautilus-extension1a amd64 1:3.4.2-0ubuntu3 [51.5 kB]
Get:15 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-nautilus-3.0 amd64 1:3.4.2-0ubuntu3 [6,178 B]
Get:16 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main gwibber amd64 3.4.2-0ubuntu1 [157 kB]
Get:17 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main gwibber-service all 3.4.2-0ubuntu1 [40.6 kB]
Get:18 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libgwibber2 amd64 3.4.2-0ubuntu1 [71.6 kB]
Get:19 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main libgwibber-gtk2 amd64 3.4.2-0ubuntu1 [64.0 kB]
Get:20 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main gwibber-service-facebook all 3.4.2-0ubuntu1 [7,760 B]
Get:21 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main gwibber-service-identica all 3.4.2-0ubuntu1 [7,778 B]
Get:22 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main gwibber-service-twitter all 3.4.2-0ubuntu1 [8,974 B]
Get:23 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main linux-libc-dev amd64 3.2.0-26.41 [863 kB]
Get:24 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus-data all 1:3.4.2-0ubuntu3 [63.4 kB]
Get:25 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus amd64 1:3.4.2-0ubuntu3 [821 kB]
Get:26 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main python-crypto amd64 2.4.1-1ubuntu0.1 [293 kB]
Get:27 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main smbclient amd64 2:3.6.3-2ubuntu2.3 [14.1 MB]
Get:28 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main samba-common all 2:3.6.3-2ubuntu2.3 [325 kB]
Get:29 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main samba-common-bin amd64 2:3.6.3-2ubuntu2.3 [6,177 kB]
Get:30 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main software-center all 5.2.3 [623 kB]
Get:31 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird-globalmenu amd64 13.0.1+build1-0ubuntu0.12.04.1 [48.0 kB]
Get:32 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird amd64 13.0.1+build1-0ubuntu0.12.04.1 [21.8 MB]
Get:33 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird-gnome-support amd64 13.0.1+build1-0ubuntu0.12.04.1 [9,200 B]
Get:34 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird-locale-en amd64 1:13.0.1+build1-0ubuntu0.12.04.1 [366 kB]
Get:35 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird-locale-en-us all 1:13.0.1+build1-0ubuntu0.12.04.1 [13.5 kB]
Get:36 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main unity-lens-video all 0.3.5-0ubuntu1.1 [8,094 B]
Get:37 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main xdiagnose all 2.5.1 [59.0 kB]
Get:38 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main xserver-xorg-input-evdev amd64 1:2.7.0-0ubuntu1.2 [33.3 kB]
Get:39 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main xserver-xorg-input-vmmouse amd64 1:12.9.0-0ubuntu0.1 [15.1 kB]
Get:40 [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) precise-updates/main gnome-settings-daemon amd64 3.4.2-0ubuntu0.2 [481 kB]
Fetched 70.7 MB in 12s (5,878 kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 226046 files and directories currently installed.)
Preparing to replace libgtk-3-bin 3.4.2-0ubuntu0.2 (using .../libgtk-3-bin_3.4.2-0ubuntu0.3_amd64.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace libgail-3-0 3.4.2-0ubuntu0.2 (using .../libgail-3-0_3.4.2-0ubuntu0.3_amd64.deb) ...
Unpacking replacement libgail-3-0 ...
Preparing to replace libgtk-3-0 3.4.2-0ubuntu0.2 (using .../libgtk-3-0_3.4.2-0ubuntu0.3_amd64.deb) ...
Unpacking replacement libgtk-3-0 ...
Preparing to replace libgtk-3-common 3.4.2-0ubuntu0.2 (using .../libgtk-3-common_3.4.2-0ubuntu0.3_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.2 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.3_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.2 (using .../libsmbclient_2%3a3.6.3-2ubuntu2.3_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace accountsservice 0.6.15-2ubuntu9 (using .../accountsservice_0.6.15-2ubuntu9.1_amd64.deb) ...
Unpacking replacement accountsservice ...
Preparing to replace libaccountsservice0 0.6.15-2ubuntu9 (using .../libaccountsservice0_0.6.15-2ubuntu9.1_amd64.deb) ...
Unpacking replacement libaccountsservice0 ...
Preparing to replace firefox-globalmenu 13.0+build1-0ubuntu0.12.04.1 (using .../firefox-globalmenu_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 13.0+build1-0ubuntu0.12.04.1 (using .../firefox_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 13.0+build1-0ubuntu0.12.04.1 (using .../firefox-gnome-support_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-locale-en 13.0+build1-0ubuntu0.12.04.1 (using .../firefox-locale-en_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace gir1.2-gtk-3.0 3.4.2-0ubuntu0.2 (using .../gir1.2-gtk-3.0_3.4.2-0ubuntu0.3_amd64.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace libnautilus-extension1a 1:3.4.2-0ubuntu2 (using .../libnautilus-extension1a_1%3a3.4.2-0ubuntu3_amd64.deb) ...
Unpacking replacement libnautilus-extension1a ...
Preparing to replace gir1.2-nautilus-3.0 1:3.4.2-0ubuntu2 (using .../gir1.2-nautilus-3.0_1%3a3.4.2-0ubuntu3_amd64.deb) ...
Unpacking replacement gir1.2-nautilus-3.0 ...
Preparing to replace gwibber 3.4.1-0ubuntu1 (using .../gwibber_3.4.2-0ubuntu1_amd64.deb) ...
Unpacking replacement gwibber ...
Preparing to replace gwibber-service 3.4.1-0ubuntu1 (using .../gwibber-service_3.4.2-0ubuntu1_all.deb) ...
Unpacking replacement gwibber-service ...
Preparing to replace libgwibber2 3.4.1-0ubuntu1 (using .../libgwibber2_3.4.2-0ubuntu1_amd64.deb) ...
Unpacking replacement libgwibber2 ...
Preparing to replace libgwibber-gtk2 3.4.1-0ubuntu1 (using .../libgwibber-gtk2_3.4.2-0ubuntu1_amd64.deb) ...
Unpacking replacement libgwibber-gtk2 ...
Preparing to replace gwibber-service-facebook 3.4.1-0ubuntu1 (using .../gwibber-service-facebook_3.4.2-0ubuntu1_all.deb) ...
Unpacking replacement gwibber-service-facebook ...
Preparing to replace gwibber-service-identica 3.4.1-0ubuntu1 (using .../gwibber-service-identica_3.4.2-0ubuntu1_all.deb) ...
Unpacking replacement gwibber-service-identica ...
Preparing to replace gwibber-service-twitter 3.4.1-0ubuntu1 (using .../gwibber-service-twitter_3.4.2-0ubuntu1_all.deb) ...
Unpacking replacement gwibber-service-twitter ...
Preparing to replace linux-libc-dev 3.2.0-25.40 (using .../linux-libc-dev_3.2.0-26.41_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace nautilus-data 1:3.4.2-0ubuntu2 (using .../nautilus-data_1%3a3.4.2-0ubuntu3_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:3.4.2-0ubuntu2 (using .../nautilus_1%3a3.4.2-0ubuntu3_amd64.deb) ...
Unpacking replacement nautilus ...
Preparing to replace python-crypto 2.4.1-1 (using .../python-crypto_2.4.1-1ubuntu0.1_amd64.deb) ...
Unpacking replacement python-crypto ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.2 (using .../smbclient_2%3a3.6.3-2ubuntu2.3_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.2 (using .../samba-common_2%3a3.6.3-2ubuntu2.3_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.2 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.3_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace software-center 5.2.2.2 (using .../software-center_5.2.3_all.deb) ...
Unpacking replacement software-center ...
Preparing to replace thunderbird-globalmenu 12.0.1+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird 12.0.1+build1-0ubuntu0.12.04.1 (using .../thunderbird_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 12.0.1+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en 1:12.0.1+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird-locale-en-us 1:12.0.1+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a13.0.1+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace unity-lens-video 0.3.5-0ubuntu1 (using .../unity-lens-video_0.3.5-0ubuntu1.1_all.deb) ...
Unpacking replacement unity-lens-video ...
Preparing to replace xdiagnose 2.5 (using .../xdiagnose_2.5.1_all.deb) ...
Unpacking replacement xdiagnose ...
Preparing to replace xserver-xorg-input-evdev 1:2.7.0-0ubuntu1 (using .../xserver-xorg-input-evdev_1%3a2.7.0-0ubuntu1.2_amd64.deb) ...
Unpacking replacement xserver-xorg-input-evdev ...
Preparing to replace xserver-xorg-input-vmmouse 1:12.8.0-1 (using .../xserver-xorg-input-vmmouse_1%3a12.9.0-0ubuntu0.1_amd64.deb) ...
Unpacking replacement xserver-xorg-input-vmmouse ...
Preparing to replace gnome-settings-daemon 3.4.1-0ubuntu1.1 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.2_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for shared-mime-info ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libgtk-3-common (3.4.2-0ubuntu0.3) ...
Setting up libgtk-3-0 (3.4.2-0ubuntu0.3) ...
Setting up libgtk-3-bin (3.4.2-0ubuntu0.3) ...
Setting up libgail-3-0 (3.4.2-0ubuntu0.3) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.3) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.3) ...
Setting up libaccountsservice0 (0.6.15-2ubuntu9.1) ...
Setting up accountsservice (0.6.15-2ubuntu9.1) ...
Setting up firefox (13.0.1+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up firefox-gnome-support (13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up gir1.2-gtk-3.0 (3.4.2-0ubuntu0.3) ...
Setting up libnautilus-extension1a (1:3.4.2-0ubuntu3) ...
Setting up gir1.2-nautilus-3.0 (1:3.4.2-0ubuntu3) ...
Setting up gwibber-service (3.4.2-0ubuntu1) ...
Setting up libgwibber2 (3.4.2-0ubuntu1) ...
Setting up libgwibber-gtk2 (3.4.2-0ubuntu1) ...
Setting up gwibber (3.4.2-0ubuntu1) ...
Setting up gwibber-service-facebook (3.4.2-0ubuntu1) ...
Setting up gwibber-service-identica (3.4.2-0ubuntu1) ...
Setting up gwibber-service-twitter (3.4.2-0ubuntu1) ...
Setting up linux-libc-dev (3.2.0-26.41) ...
Setting up nautilus-data (1:3.4.2-0ubuntu3) ...
Setting up nautilus (1:3.4.2-0ubuntu3) ...
Setting up python-crypto (2.4.1-1ubuntu0.1) ...
Setting up samba-common (2:3.6.3-2ubuntu2.3) ...
Setting up smbclient (2:3.6.3-2ubuntu2.3) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.3) ...
Setting up software-center (5.2.3) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Setting up thunderbird (13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-globalmenu (13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up unity-lens-video (0.3.5-0ubuntu1.1) ...
Setting up xdiagnose (2.5.1) ...
Setting up xserver-xorg-input-evdev (1:2.7.0-0ubuntu1.2) ...
Setting up xserver-xorg-input-vmmouse (1:12.9.0-0ubuntu0.1) ...
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
milan@milan-desktop:~$

---

### Post by Old_Grey_Wolf on 2012-06-30
That actually looks like it didn't have errors. Three packages were kept back.

If you enter this command you will get the 3 packages that were kept back (not upgraded). They are kernel upgrades that a simple apt-get upgrade doesn't upgrade. To upgrade kernel packages you need to use this command: ```
sudo apt-get dist-upgrade
```

---

### Post by thx1137 on 2012-07-07
Ok, I did

sudo apt-get dist-upgrade
it went without errors.

I tried to debug the distro.py script loop which is on the line no. 78, which lists all  the templates read from the sources.list file. I found that the following names are in the list:
```

squeeze
squeeze-proposed-updates
squeeze/updates
lenny
lenny-proposed-updates
lenny/updates
etch
etch-proposed-updates
etch/updates
sarge
sarge-proposed-updates
sarge/updates
stable
testing
sid
unstable
parkes
parkes/updates
deltah
deltah-security
deltah-updates
deltah-backports
precise
precise
precise
precise
precise
precise-security
precise-security
precise-updates
precise-updates
precise-proposed
precise-proposed
precise-backports
precise-backports
oneiric
oneiric
oneiric
oneiric
oneiric
oneiric-security
oneiric-security
oneiric-updates
oneiric-updates
oneiric-proposed
oneiric-proposed
oneiric-backports
oneiric-backports
natty
natty
natty
natty
natty
natty-security
natty-security
natty-updates
natty-updates
natty-proposed
natty-proposed
natty-backports
natty-backports
maverick
maverick
maverick
maverick
maverick-security
maverick-updates
maverick-proposed
maverick-backports
lucid
lucid
lucid-security
lucid-updates
lucid-proposed
lucid-backports
karmic
karmic
karmic-security
karmic-updates
karmic-proposed
karmic-backports
jaunty
jaunty
jaunty-security
jaunty-updates
jaunty-proposed
jaunty-backports
intrepid
intrepid
intrepid-security
intrepid-updates
intrepid-proposed
intrepid-backports
hardy
hardy
hardy-security
hardy-updates
hardy-proposed
hardy-backports
gutsy
gutsy
gutsy-security
gutsy-updates
gutsy-proposed
gutsy-backports
feisty
feisty
feisty-security
feisty-updates
feisty-proposed
feisty-backports
edgy
edgy
edgy-security
edgy-updates
edgy-proposed
edgy-backports
dapper
dapper
dapper-security
dapper-updates
dapper-proposed
dapper-backports
breezy
breezy
breezy-security
breezy-updates
breezy-backports
hoary
hoary
hoary-security
hoary-updates
hoary-backports
warty
warty
warty-security
warty-updates
warty-backports
```

but the name which these are matched against is

```
quantal
``` , which is not found and therefore the exception is raised.

so how do I interpret this? I somehow upgraded to Quantal Quetzal, but the repositories I have in sources.list do not have it? I did not do anything fancy with my Ubuntu install. I was just regularly updating the system when there were updates available and I installed few apps, nothing more. No tinkering with system files or anything like that.

---

### Post by thx1137 on 2012-07-07
I suspect this could be the same issue as reported here [http://askubuntu.com/questions/126498/12-04-reports-itself-as-quantal-after-installing-the-toolchain-test-ppa](http://askubuntu.com/questions/126498/12-04-reports-itself-as-quantal-after-installing-the-toolchain-test-ppa) , because I too have gcc-4.7

---

### Post by thx1137 on 2012-07-07
Ok, I confirm that the marked solution in the above link fixed the issue.

---

